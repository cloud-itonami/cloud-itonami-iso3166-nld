(ns statute.facts
  "General-law compliance catalog for the Netherlands (NLD) -- extends
  this repo's existing `marketentry.facts` (public-procurement market-
  entry only, narrow scope) with a second, orthogonal catalog of
  statutes a company generally must track for compliance. Mirrors
  cloud-itonami-iso3166-jpn/-usa/-gbr/-deu/-fra/-can/-aus/-kor's
  `statute.facts` (ADR-2607141700, cloud-itonami-compliance-fact-federation).

  Every entry cites an OFFICIAL wetten.overheid.nl (Dutch government
  legislation portal) URL -- never fabricated. A law not in this table
  has NO spec-basis, full stop; extend `catalog`, do not invent an
  id/url. Title for every entry below was directly WebFetch-verified
  against the live wetten.overheid.nl page on 2026-07-15 (rendered
  cleanly, like the UK/DE/AU/CA sources).")

(def catalog
  "iso3 -> vector of statute entries."
  {"NLD"
   [{:statute/id "nld.burgerlijk-wetboek-boek-2"
     :statute/title "Burgerlijk Wetboek Boek 2, Rechtspersonen (Civil Code Book 2, Legal Entities)"
     :statute/jurisdiction "NLD"
     :statute/kind :law
     :statute/law-number "BWBR0003045"
     :statute/url "https://wetten.overheid.nl/BWBR0003045"
     :statute/url-provenance :official-wetten-overheid-nl
     :statute/retrieved-at "2026-07-15"
     :statute/topic #{:corporate-governance :incorporation}}
    {:statute/id "nld.uitvoeringswet-avg"
     :statute/title "Uitvoeringswet Algemene verordening gegevensbescherming (GDPR Implementation Act)"
     :statute/jurisdiction "NLD"
     :statute/kind :law
     :statute/law-number "BWBR0040940"
     :statute/url "https://wetten.overheid.nl/BWBR0040940"
     :statute/url-provenance :official-wetten-overheid-nl
     :statute/enacted-date "2018-05-16"
     :statute/retrieved-at "2026-07-15"
     :statute/topic #{:data-protection :privacy}}
    {:statute/id "nld.arbeidstijdenwet"
     :statute/title "Arbeidstijdenwet (Working Hours Act)"
     :statute/jurisdiction "NLD"
     :statute/kind :law
     :statute/law-number "BWBR0007671"
     :statute/url "https://wetten.overheid.nl/BWBR0007671"
     :statute/url-provenance :official-wetten-overheid-nl
     :statute/enacted-date "1995-11-23"
     :statute/retrieved-at "2026-07-15"
     :statute/topic #{:labor :employment}}]})

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
      :note (str "cloud-itonami-iso3166-nld statute.facts Wave 0 (ADR-2607141700): "
                 (count (get catalog "NLD")) " NLD statutes seeded with an "
                 "official wetten.overheid.nl citation. Extend "
                 "`statute.facts/catalog`, never fabricate a law-id or URL.")})))

(defn by-topic [iso3 topic]
  (filterv #(contains? (:statute/topic %) topic) (spec-basis iso3)))
