
CPU -> Central Processing Unit

Quando dizemos que uma CPU tem 4 núcleos thread isso significa, que fisicamente existem 4 núcleos na CPU e cada núcleo pode simular ` N núcleos lógicos` que podem variar de 2/4/6 até 8 que seriam os hig end do mercado. 

Uma CPU com 4 núcleos e 8 threads geralmente está utilizando a tecnologia ==**hyper-threading**== (ou uma tecnologia semelhante), o que permite a cada núcleo físico simular dois núcleos lógicos. Isso faz com que o processador pareça ter o dobro de threads, mas não dobra a performance de fato, apenas melhora o aproveitamento do tempo ocioso dos núcleos.

Portanto, nesse caso, cada núcleo pode executar **duas threads** em paralelo, o que cria o efeito de "2 linhas de execução" por núcleo. Assim, uma CPU de 4 núcleos e 8 threads pode executar 8 threads de forma simultânea, mas a capacidade de processamento real ainda está limitada pelos 4 núcleos físicos.