# 并查集

## 简介

并查集是一种数据结构, 常用于描述集合,经常用于解决此类问题:某个元素是否属于某个集合,或者 某个元素 和 另一个元素是否同属于一个集合。

## 思路

1. 通过实现类似树形结构，将所有有关系的元素连接，形成一个关系族。
2. 最终形成多棵树。
3. 多棵树的结构有助于解决数据中多关系的情况。

## 模版

JAVA代码实现如下：

```
class UnionFind {
    /**
     * All elements.
     */
    private ArrayList<Integer> elementList = new ArrayList<>();
    /**
     * Every element's weight.
     */
    private ArrayList<Integer> weightList = new ArrayList<>();
    /**
     * The size of this UnionFind.
     */
    private Integer size;

    /**
     * Instantiates a new Union find.
     *
     * @param initialValue the initial value
     */
    public UnionFind(Integer initialValue) {
        this.size = initialValue;
        for (int i = 0; i < initialValue; ++i) {
            elementList.add(i);
            weightList.add(i);
        }
    }

    /**
     * Find the input element's top parent in the UnionFind tree.
     *
     * @param element input element
     * @return the top element in the UnionFind tree
     */
    private Integer find(Integer element) {
        while (!element.equals(elementList.get(element))) {
            elementList.add(element, elementList.get(element));
            element = elementList.get(element);
        }
        return element;
    }

    /**
     * Union two element.
     *
     * @param current current element
     * @param dest    destination element
     */
    private void union(Integer current, Integer dest) {
        Integer currentRoot = find(current);
        Integer destRoot = find(dest);

        if (currentRoot.equals(destRoot)) {
            return;
        }

        if (weightList.get(currentRoot) > weightList.get(destRoot)) {
            elementList.add(currentRoot, destRoot);
            weightList.add(current, weightList.get(current) + weightList.get(destRoot));
        } else {
            elementList.add(destRoot, currentRoot);
            weightList.add(destRoot, weightList.get(destRoot) + weightList.get(current));
        }
    }

    /**
     * Get num of all the element which weight is 1.
     *
     * @return the num of all the element which weight is 1
     */
    private Integer getRoots() {
        AtomicInteger rootSize = new AtomicInteger(1);
        weightList.forEach(weight -> {
            if (weight == 1) {
                rootSize.addAndGet(1);
            }
        });
        return rootSize.intValue();
    }
}
```