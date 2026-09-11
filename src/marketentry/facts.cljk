(ns marketentry.facts "Netherlands market-entry catalog.")
(def catalog
  {"NLD" {:name "Netherlands"
          :owner-authority "PIANOo / TenderNed"
          :legal-basis "Aanbestedingswet 2012; EU procurement directives"
          :national-spec "TenderNed supplier registration + KvK / BTW"
          :provenance "https://www.tenderned.nl/"
          :required-evidence ["KvK extract"
                              "TenderNed registration record"
                              "BTW-nummer record"
                              "Authorized-representative record"]
          :rep-owner-authority "contracting authorities / TenderNed"
          :rep-legal-basis "EU establishment or authorized representative for many procedures"
          :rep-provenance "https://www.tenderned.nl/"
          :corporate-number-owner-authority "KVK / Belastingdienst"
          :corporate-number-legal-basis "KvK-nummer / BTW-identificatienummer"
          :corporate-number-provenance "https://www.kvk.nl/"}
   "USA" {:name "United States" :owner-authority "GSA/SAM.gov" :legal-basis "FAR"
          :national-spec "SAM.gov" :provenance "https://sam.gov/"
          :required-evidence ["EIN record" "SAM.gov registration record" "State business registration record" "SAM UEI verification record"]}
   "DEU" {:name "Germany" :owner-authority "e-Vergabe" :legal-basis "GWB/VgV"
          :national-spec "e-Vergabe" :provenance "https://www.evergabe-online.de/"
          :required-evidence ["Handelsregister extract" "e-Vergabe registration record" "USt-IdNr record" "Authorized-representative record"]}
   "FRA" {:name "France" :owner-authority "PLACE" :legal-basis "Code de la commande publique"
          :national-spec "PLACE" :provenance "https://www.economie.gouv.fr/daj/commande-publique"
          :required-evidence ["SIRET/SIREN record" "PLACE registration record" "TVA record" "Authorized-representative record"]}})

(defn spec-basis [iso3] (get catalog iso3))
(defn coverage
  ([] (coverage (keys catalog)))
  ([iso3s]
   (let [have (filter catalog iso3s) missing (remove catalog iso3s)]
     {:requested (count iso3s) :covered (count have)
      :covered-jurisdictions (vec (sort have))
      :missing-jurisdictions (vec (sort missing))
      :note "R0 catalog seed"})))
(defn required-evidence-satisfied? [iso3 submitted]
  (when-let [{:keys [required-evidence]} (spec-basis iso3)]
    (= (count required-evidence) (count (filter (set submitted) required-evidence)))))
(defn evidence-checklist [iso3] (:required-evidence (spec-basis iso3) []))
(defn rep-spec-basis [iso3]
  (when-let [sb (spec-basis iso3)]
    (when (:rep-owner-authority sb)
      (select-keys sb [:rep-owner-authority :rep-legal-basis :rep-provenance]))))
(defn corporate-number-spec-basis [iso3]
  (when-let [sb (spec-basis iso3)]
    (when (:corporate-number-owner-authority sb)
      (select-keys sb [:corporate-number-owner-authority :corporate-number-legal-basis :corporate-number-provenance]))))
