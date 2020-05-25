# 对于 display:none 的元素，其子元素中的a/button只会采集一次浏览量，但是想每次曝光都采集一次浏览量怎么处理？

web sdk 只有 DOM 结构改变的时候才会发送元素浏览量，而由 display 控制显隐并不会引起 DOM 结构的改变，所以要想每次曝光都采集一次 imp，试试 createElement 和 removeElement，但是频繁的话会影响性能哦。

