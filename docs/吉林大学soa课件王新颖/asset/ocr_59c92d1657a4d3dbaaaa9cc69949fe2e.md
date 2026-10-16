# Services 集合示例cont.

+   - S1={<input,name,"isbn">,
+     <input,message," GetBookPriceRequest">}
+   - S2={<output,name,"isbn">,
+     <output,message," GetBookPriceResponse">}
+   - S3={<operation,name,"getBookPrice">}∪{S1}∪{S2}
+   - S4={<portType,name,"BookQuote">}∪{S3}