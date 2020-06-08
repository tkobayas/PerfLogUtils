Results
=====

7.38.0-SNAPSHOT (No PerfLogUtils)

@Warmup(iterations = 1000)
@Measurement(iterations = 500)

Benchmark                        (asyncInserts)  (cep)  (factsNr)  (joinsNr)  (multithread)  (rulesNr)  Mode   Cnt   Score   Error  Units
FireOnlyWithJoinsBenchmark.test           false  false         15          3          false         32    ss  1000  25.793 ± 0.222  ms/op

Benchmark                        (factsNr)  (joinsNr)  (perfLog)  (rulesNr)  Mode   Cnt   Score   Error  Units
FireOnlyWithJoinsBenchmark.test         15          3      false         32    ss  1000  26.006 ± 0.167  ms/op

--

7.38.0-SNAPSHOT-perf

Benchmark                        (asyncInserts)  (cep)  (factsNr)  (joinsNr)  (multithread)  (rulesNr)  Mode   Cnt   Score   Error  Units
FireOnlyWithJoinsBenchmark.test           false  false         15          3          false         32    ss  1000  24.876 ± 0.139  ms/op

Benchmark                        (factsNr)  (joinsNr)  (perfLog)  (rulesNr)  Mode   Cnt   Score   Error  Units
FireOnlyWithJoinsBenchmark.test         15          3       true         32    ss  2000  26.316 ± 0.154  ms/op
FireOnlyWithJoinsBenchmark.test         15          3      false         32    ss  2000  25.856 ± 0.147  ms/op

=====

- 7.38.0-SNAPSHOT perfLog=false vs 7.38.0-SNAPSHOT-perf perfLog=false

  26.006 vs 25.856

  -> There is no overhead introduced by disabled PerfLogUtils
 
- 7.38.0-SNAPSHOT-perf perfLog=false vs 7.38.0-SNAPSHOT-perf perfLog=true

  25.856 vs 26.316

  -> Even if perfLog is enabled (just calculation, without logging), the difference is small (less than 3%) so it wouldn't likely interfere performance analysis.