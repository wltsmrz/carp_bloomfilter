# carp_bloomfilter

(Unsophisticated) Bloomfilter for carp using [carp_bitset](https://github.com/wltsmrz/carp_bitset) and [carp_murmurhash3](https://github.com/wltsmrz/carp_murmurhash3)

```clojure
(load "https://github.com/wltsmrz/carp_bloomfilter@v0.0.1")

(def false-positive-rate 0.5)
(def elements-count 2)
(def b (BloomFilter.init false-positive-rate elements-count))
(def str1 "alright")
(def str2 "ok")
(def str3 "nalright")
(def str4 "nok")

(defn-do main []
 (BloomFilter.add &b (String.to-bytes str1))
 (BloomFilter.add &b (String.to-bytes str2))

 (IO.println &(Bool.str (BloomFilter.contains? &b (String.to-bytes str1))))
 (IO.println &(Bool.str (BloomFilter.contains? &b (String.to-bytes str2))))

 (IO.println &(Bool.str (BloomFilter.contains? &b (String.to-bytes str3))))
 (IO.println &(Bool.str (BloomFilter.contains? &b (String.to-bytes str4))))
)

```
