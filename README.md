# konserve-faraday

A [DynamoDB](https://aws.amazon.com/dynamodb/) backend for [konserve](https://github.com/replikativ/konserve-carmine) implemented with [faraday](https://github.com/Taoensso/faraday).

The purpose of konserve is to have a unified associative key-value interface for edn datastructures and binary blobs. Use the standard interface functions of konserve.

# Status

![master](https://github.com/alekcz/konserve-faraday/workflows/master/badge.svg) [![codecov](https://codecov.io/gh/alekcz/konserve-faraday/branch/master/graph/badge.svg)](https://codecov.io/gh/alekcz/konserve-faraday) 

## Usage

_Link to the your lib on clojars_

`[alekcz/store "0.1.0-SNAPSHOT"]`

```clojure
(require '[konserve-faraday.core :refer :all]
         '[clojure.core.async :refer [<!!] :as async]
         '[konserve.core :as k])
  
  (def your-store (<!! (new-faraday-store connection-uri :other-config "info" :and-more :yay)))

  (<!! (k/exists? your-store  "cecilia"))
  (<!! (k/get-in your-store ["cecilia"]))
  (<!! (k/assoc-in your-store ["cecilia"] 28))
  (<!! (k/update-in your-store ["cecilia"] inc))
  (<!! (k/get-in your-store ["cecilia"]))

  (defrecord Test [a])
  (<!! (k/assoc-in your-store ["agatha"] (Test. 35)))
  (<!! (k/get-in your-store ["agatha"]))
```

## License

Copyright © 2020 Alexander Oloo

This program and the accompanying materials are made available under the
terms of the Eclipse Public License 2.0 which is available at
http://www.eclipse.org/legal/epl-2.0.

This Source Code may also be made available under the following Secondary
Licenses when the conditions for such availability set forth in the Eclipse
Public License, v. 2.0 are satisfied: GNU General Public License as published by
the Free Software Foundation, either version 2 of the License, or (at your
option) any later version, with the GNU Classpath Exception which is available
at https://www.gnu.org/software/classpath/license.html.
