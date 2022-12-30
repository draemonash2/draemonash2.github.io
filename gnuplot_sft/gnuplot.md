[トップに戻る](../index.md)

# Tips

- シェルからplotする方法

```shell
gnuplot << EOF
set terminal png noenhanced
set output "test.png"
set ylabel 'execution time [s]'
set xlabel 'ros time'
set key font"Arial,9"
set noxtics
plot \
    "< cat plotdata_aaa.log" w l title "aaa"
    "< cat plotdata_bbb.log" w l title "bbb"
    "< cat plotdata_ccc.log" w l title "ccc"
    "< cat plotdata_ddd.log" w l title "ddd"
EOF
```

[トップに戻る](../index.md)
