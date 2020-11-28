# carp_bloomfilter

(Unsophisticated) Bloomfilter for carp using [carp_bitset](https://github.com/wltsmrz/carp_bitset) and [carp_murmurhash3](https://github.com/wltsmrz/carp_murmurhash3)

```clojure
(load "https://github.com/wltsmrz/carp_bloomfilter@v0.0.4")

(def false-positive-rate 0.5)
(def elements-count 2)

(def bloomfilter (BloomFilter.init false-positive-rate elements-count))

(def str1 (String.to-bytes "alright"))
(def str2 (String.to-bytes "ok"))
(def str3 (String.to-bytes "nalright"))
(def str4 (String.to-bytes "nok"))

(defn-do main []
 (BloomFilter.add &bloomfilter @&str1)
 (BloomFilter.add &bloomfilter @&str2)

 (IO.println &(Bool.str (BloomFilter.contains? &bloomfilter @&str1)))
 (IO.println &(Bool.str (BloomFilter.contains? &bloomfilter @&str2)))

 (IO.println &(Bool.str (BloomFilter.contains? &bloomfilter @&str3)))
 (IO.println &(Bool.str (BloomFilter.contains? &bloomfilter @&str4)))
)

```
