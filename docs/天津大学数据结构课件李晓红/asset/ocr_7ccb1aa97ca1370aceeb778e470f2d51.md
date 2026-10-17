```
for ( i = 0; i < n; i++ ) {//逐个顶点求各活动的e[k]和l[k]
p = NodeTable[i].adj; //该顶点边链表链头指针p
while ( p != NULL ) {
k = p→dest; //k是i的后继邻接顶点
e = Ve[i]; l = Vl[k] - p→cost;
if ( l == e )//关键活动
cout << "<" << i << "," << k
<< ">" << "是关键活动" << endl;
p = p→link; //找下一个后继
}
}
}
}
```