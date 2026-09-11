(ns culture.facts
  "Country-level regional-culture catalog for the Netherlands (NLD) --
  national dishes, protected products, beverages, crafts, festivals and
  heritage sites, per ADR-2607171400 addendum 2 (cloud-itonami-municipality-
  culture-catalog Wave 1, in com-junkawasaki/root). Sibling namespace to
  `marketentry.facts` / `statute.facts` (ADR-2607141700); city-level
  counterparts live in the cloud-itonami-municipality-* repos.

  Catalog is keyed by UPPERCASE ISO3 (mirrors `statute.facts`); entries
  carry no :culture/municipality (that attribute is city-level only).

  Every entry cites a source URL that was actually fetched and read on
  :culture/retrieved-at -- never fabricated. Summaries state only what the
  cited source confirms. An item not in this table has NO spec-basis, full
  stop; extend `catalog`, do not invent an id/url.")

(def catalog
  "iso3 -> vector of culture entries."
  {"NLD"
   [{:culture/id "nld.dish.stroopwafel"
     :culture/name "Stroopwafel"
     :culture/country "NLD"
     :culture/kind :dish
     :culture/summary "Thin, round Dutch biscuit made from two layers of baked dough joined by a caramel/treacle syrup filling; originated in Gouda, South Holland."
     :culture/url "https://en.wikipedia.org/wiki/Stroopwafel"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nld.dish.bitterballen"
     :culture/name "Bitterballen"
     :culture/country "NLD"
     :culture/kind :dish
     :culture/summary "Dutch meat-based snack made from a thick beef or veal stew, chilled, rolled into balls, breaded, deep-fried, and traditionally served with mustard."
     :culture/url "https://en.wikipedia.org/wiki/Bitterballen"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nld.dish.stamppot"
     :culture/name "Stamppot"
     :culture/country "NLD"
     :culture/kind :dish
     :culture/summary "Traditional Dutch dish of potatoes mashed with one or several vegetables, typically garnished with sausage."
     :culture/url "https://en.wikipedia.org/wiki/Stamppot"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nld.dish.poffertjes"
     :culture/name "Poffertjes"
     :culture/country "NLD"
     :culture/kind :dish
     :culture/summary "Traditional Dutch batter cakes made with yeast and flour, resembling small fluffy pancakes, typically served with powdered sugar and butter."
     :culture/url "https://en.wikipedia.org/wiki/Poffertjes"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nld.beverage.jenever"
     :culture/name "Jenever"
     :culture/country "NLD"
     :culture/kind :beverage
     :culture/summary "Juniper-flavoured traditional liquor produced in the Netherlands and adjoining regions of Belgium, France and Germany; the historical ancestor of modern gin."
     :culture/url "https://en.wikipedia.org/wiki/Jenever"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nld.product.gouda-cheese"
     :culture/name "Gouda cheese"
     :culture/country "NLD"
     :culture/kind :product
     :culture/summary "Family of yellow cow's-milk cheeses originally from the Netherlands, named after the city of Gouda in South Holland where it was historically traded."
     :culture/url "https://en.wikipedia.org/wiki/Gouda_cheese"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nld.product.edam-cheese"
     :culture/name "Edam cheese"
     :culture/country "NLD"
     :culture/kind :product
     :culture/summary "Semi-hard cheese that originated in the Netherlands, named after the town of Edam in North Holland, traditionally sold in wax-coated spheres."
     :culture/url "https://en.wikipedia.org/wiki/Edam_cheese"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nld.craft.delftware"
     :culture/name "Delftware"
     :culture/country "NLD"
     :culture/kind :craft
     :culture/summary "Dutch tin-glazed earthenware, known for its blue-and-white designs, that originated in and takes its name from the city of Delft."
     :culture/url "https://en.wikipedia.org/wiki/Delftware"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nld.festival.koningsdag"
     :culture/name "King's Day"
     :culture/name-local "Koningsdag"
     :culture/country "NLD"
     :culture/kind :festival
     :culture/summary "Annual Dutch national holiday celebrated on 27 April (26 April if the 27th falls on a Sunday) marking the reigning monarch's birthday, observed throughout the Kingdom of the Netherlands with orange-themed festivities and street markets."
     :culture/url "https://en.wikipedia.org/wiki/Koningsdag"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "nld.heritage.kinderdijk"
     :culture/name "Kinderdijk"
     :culture/country "NLD"
     :culture/kind :heritage
     :culture/summary "Group of 19 eighteenth-century windmills near Kinderdijk in South Holland, built around 1740 to drain the Alblasserwaard polder, inscribed as a UNESCO World Heritage Site in 1997."
     :culture/url "https://en.wikipedia.org/wiki/Kinderdijk"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}]})

(defn spec-basis [iso3] (get catalog iso3))

(defn coverage
  ([] (coverage (keys catalog)))
  ([iso3s]
   (let [have (filter catalog iso3s)
         missing (remove catalog iso3s)]
     {:requested (count iso3s)
      :covered (count have)
      :covered-jurisdictions (vec (sort have))
      :missing-jurisdictions (vec (sort missing))
      :note (str "cloud-itonami-iso3166-nld culture catalog "
                 "(ADR-2607171400 addendum 2, Wave 1): " (count (get catalog "NLD"))
                 " NLD entries, each with a fetched-and-read citation. "
                 "Extend `culture.facts/catalog`, never fabricate an id/url.")})))

(defn by-kind [iso3 kind]
  (filterv #(= (:culture/kind %) kind) (spec-basis iso3)))
