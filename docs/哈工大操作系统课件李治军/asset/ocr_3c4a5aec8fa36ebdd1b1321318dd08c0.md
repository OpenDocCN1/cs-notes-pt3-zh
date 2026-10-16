# put_page

```
//在linux/mm/memory.c中
unsigned long put_page(unsigned long page, //物理地址
    unsigned long address)
{ unsigned long tmp, *page_table;
page_table=(unsigned long *)((address>>20)&ffc);
if ((*page_table)&1)
    page_table=(unsigned long*)(0xfffff000&*page_table);
else{
    tmp=get_free_page();
    *page_table=tmp|7;
    page_table=(unsigned long*)tmp;}
page_table[(address>>12)&0x3ff] = page|7;
return page;
}
```