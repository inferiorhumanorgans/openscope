# Aircraft Format

## Example Aircraft File

```javascript
{
    "name": "Boeing 747-400",
    "icao": "B744",
    "engines": {
        "number": 4,
        "type": "J"
    },
    "weightClass": "H",
    "category": {
        "srs": 3,
        "lahso": 10,
        "recat": "B"
    },
    "ceiling": 45000,
    "rate": {
        "climb":      1500,
        "descent":    3000,
        "accelerate": 4,
        "decelerate": 2
    },
    "runway": {
        "takeoff": 3.300,
        "landing": 2.130
    },
    "speed":{
        "min":     135,
        "landing": 150,
        "cruise":  492,
        "cruiseM": 0.81,
        "max":     507,
        "maxM":    0.83
    },
    "capability": {
        "ils": true,
        "fix": true 
    }
}
```

## Property Descriptions

All properties in this section are required unless otherwise noted

* **name** – Official name of the aircraft¹ 

* **icao** – ICAO identifier of the aircraft¹

* **engines**
    ```json
    "engines": {
        "number": 4,
        "type": "J"
    }
    ```
    * **number** – Number of Engines¹
    * **type** – Engines type¹: J = Jet / T = TurboProp / P = Piston

* **weightClass** – ICAO (*not UK or Consolidated Wake Turbulence Category*) wake turbulence category¹: L = Light, L/M = Light or Medium, M = Medium, H = Heavy, J = Super (A380)

* **category**
    ```json
    "category": {
        "srs": 3,
        "lahso": 10,
        "recat": "B"
    }
    ```
    * **srs** – Same Runway Separation Category²: 1–3
    * **lahso** – LAHSO (land-and-hold-short) Category²: 1–10, *if unavailable use null*
    * **recat** – Wake Turbulence Recategorization 2.0 Appendix A Group²: A–G

* **ceiling** – Service Ceiling (feet)³

* **rate**
    ```json
    "rate": {
        "climb":      1500,
        "descent":    3000,
        "accelerate": 4,
        "decelerate": 2
    }
    ```
    * **climb** – Climb Rate (feet per minute)³
    * **descent** – Descent Rate (feet per minute)³
    * **accelerate** – Accelerate Rate (your best estimate): ~1–5
    * **decelerate** – Decelerate Rate (your best estimate): ~1–5

* **runway**
    ```json
    "runway": {
        "takeoff": 3.300,
        "landing": 2.130
    },
    ```
    * **takeoff** – Takeoff Distance Required³ (km)
    * **landing** – Landing Distance Required³ (km)

* **speed**
    ```json
    "speed":{
        "min":     135,
        "landing": 150,
        "cruise":  492,
        "cruiseM": 0.81,
        "max":     507,
        "maxM":    0.83
    },
    ```
    * **min** – Stall speed³ (Vs)
    * **landing** – Landing speed³ at threshold (Vref)
    * **cruise** – Typical cruise speed³, knots (Vc), a/c will fly at slower of this or Mc
    * **cruiseM** – Typical cruise speed³, mach (Mc), a/c will fly at slower of this or Vc, *if unavailable use null*
    * **max** – Maximum Operating Limit Speed⁴, knots (Vmo)
    * **maxM** – Maximum Operating Limit Mach⁴, mach (Mmo), *if unavailable use null*

* **capability**
    ```json
    "capability": {
        "ils": true,
        "fix": true
    }
    ```
    * **ils** – true / false, whether aircraft has ILS equipment
    * **fix** – true / false, whether aircraft has VOR or GPS equipment

## Notes

Recommended sources:

1. [https://www.icao.int/publications/DOC8643/Pages/Search.aspx](https://www.icao.int/publications/DOC8643/Pages/Search.aspx)
1. [https://www.faa.gov/documentLibrary/media/Order/2017-03-07_FAA_Order_JO_7360.1B_Aircraft_Type_Designators.pdf](https://www.faa.gov/documentLibrary/media/Order/2017-03-07_FAA_Order_JO_7360.1B_Aircraft_Type_Designators.pdf)
1. [https://contentzone.eurocontrol.int/aircraftperformance/default.aspx](https://contentzone.eurocontrol.int/aircraftperformance/default.aspx)
1. [https://www.easa.europa.eu/document-library/type-certificates](https://www.easa.europa.eu/document-library/type-certificates) or [http://www1.airweb.faa.gov/Regulatory_and_Guidance_Library/rgMakeModel.nsf/MainFrame?OpenFrameSet](http://www1.airweb.faa.gov/Regulatory_and_Guidance_Library/rgMakeModel.nsf/MainFrame?OpenFrameSet)
(Try to find the correct .pdf file and search for "Vmo" or "Mmo")
