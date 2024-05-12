# what happend here?

## What i was wondering?

I was wondering, how far i could take fibonacci with Javascript.
This led to the finding, that ```Javascript``` is very limited in the maximal size of an Integer,
so i tried to virtualize a huge number by subdeviding it to smaller portions.

First i parsed a numerical value to a ```string``` if necessary, after that i tried to tranfer this string to an array containing the number

now i serially parse the reversed arrays by adding them together and reversing it again



## Result

### The First Implementation:

the finding at the end is, that this way of trying to calculate the next fibonacci number it blew up the vm heap after 35 findings

```ps1
> node index.js
Fibonacci: 2
Fibonacci: 3 
Fibonacci: 5 
Fibonacci: 8 
Fibonacci: 10
Fibonacci: 18
Fibonacci: 28
Fibonacci: 40
Fibonacci: 68
Fibonacci: 108
Fibonacci: 170
Fibonacci: 278
Fibonacci: 408
Fibonacci: 680
Fibonacci: 1088
Fibonacci: 1708
Fibonacci: 2790
Fibonacci: 4098
Fibonacci: 6808
Fibonacci: 10900
Fibonacci: 17008
Fibonacci: 27908
Fibonacci: 40910
Fibonacci: 68018
Fibonacci: 108928
Fibonacci: 170940
Fibonacci: 279068
Fibonacci: 400008
Fibonacci: 679070
Fibonacci: 1079078
Fibonacci: 1700108
Fibonacci: 2779180
Fibonacci: 4079288
Fibonacci: 6800408
Fibonacci: 10879690
```

### The new One

The new Implementation gave back the control of Javascripts Memory Allocation to the node enviroment, wich yielded in the finding, that some clever guys at google were much smarter than i was in that case.


look at this huge number, i cannot even name:

```ps1
> node index.js
This calculation Took 26 ms
Running since: 169695
Iteration: 11260
Output Lenght: 2252
Fibonacci: 40989776700000002991000999890970970889986999179997919999990005190040970010000029990080050810800079869990780680698010980001000288001089098291801089280027900999509004079287000000027997900000040999940006997068000010001068000102000004079309999409898000801979690999798100004088080000107079980097001000170790780001710906840000001090000680040001099991810009400197000276999999879997000100010009982999800170997000000000809998000801779070300069791800000290000009804079980672889199900009700998840199918010870000010819979090000070000000400004000790000000000000000006809007001088980407019990000680000170000018001704008900009008089028897004008699907400068090009989289107400002790770019982999999990682790878840079287927907929928791998000998890000101900000070002980000040870000000000000170099877000000000007909800279068001090000000001081900000000680097090199000099970894000000080000000000000067500089008929970902800800190000000040980407998998910990000180009800409927907989000001700087998000000680000080070200000000900408799999799999699999999700290700180000040999998700000090010001000006898010089998800409897817000002710000000000028006802998407098000279001009091998298170940089400069087999990070000000000020001090098090010740069704000002700008010000000004000000710001780000027910006770940004000109999994009999783074000680000000700000009980109707899791904099991009900004009997097080086917279099907980400710780680009828900000407928981707890000170700198999990409799790999270000000000000019929798170700010899900000999699929729806796910007999990080000000827999730998199906910979790797000040090000009004088029700000017000100969987999180000990007007298700008929806800099972800680189000001000178170099810000006800407901700999700006800407000001999999999898770699999900010970801090099999999999900108000004079289817019000009000000308000000679070010892700009898699809800000000020009990000006999998999997279100090018007999068004000079998709701700010790699699870000408108107940999006790000790800080000810970000098001092998508999999840989710798040079809001879768029985079097081000070001709800000090983080810800690200080970840810800090982850970800690183090970840810200690982850810840690183080982840810200090182850810800810183080970850810200090983080810800690200080970840810800170010740
```



## Assumption

It would be interesting, if i could find a way, to optimize this using Javascript