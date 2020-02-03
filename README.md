# js-algorythm-shuffle
Algorythms to shuffle Array in Javascript with Benchmark

### Generic code
```typescript
function ArrayGenerator (nbSortableItems: number, rangeLimit: number = 1001): Sortable {
  const T = [];
  for (let i = 0; i < nbSortableItems; i++) {
    T.push(Math.floor(Math.random() * rangeLimit));
  }

  return T;
}

function swap (obj: Sortable, i: number, j: number): void {
  [obj[i], obj[j]] = [obj[j], obj[i]];
}
```

### Shuffle with Sorting Coast
Principe: for every items of an Array generate a random number and order this random list to shuffle the original array.

```typescript
function ShuffleWithSorting (list: any[]): void {
  let listObjRef = {};
  let shuffleIndexes = number[];
  for (let i = 0, l = list.length; i < l; i++) {
    shuffleIndexes[i] = Math.random();
    listObjRef[shuffleIndexes[i]] = list[i];
  }
  
  shuffleIndexes.sort(a, b => a - b);
  for (let i = 0, l = shuffleIndexes.length; i < l; i++) {
    list[i] = listObjRef[shuffleIndexes[i]];
  }
}
```

### Linear shuffle
Principle: for every item, generate a random number into the range of 0 and the current pointer position and shuffle the current pointer position value with the item at the random index.

```typescript
function randomBetween (min, max): number {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

function swap (list: any[], i, j): void {
  [list[j], list[i]] = [];
}

function LinearShuffle (list: ayn[]): void {
  for (let i = 0, l = list.length; i < l; i++) {
    const random = randomBetween(0, i);
    swap(list, i, random);
  }
}
```

