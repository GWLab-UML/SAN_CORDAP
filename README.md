# COL_CORDAP

## File types
* Colony data files contain information about coral colonies, including tag number, measurements, date recorded diseased and if a colony has been treated with antibiotics. 
* Sample data files contain information about samples collected from colonies (multiple samples can be collected at different timepoints from the same colonies)
* Antibiotic treatment files contain information on if a colony has been treated with antibiotics, when it was treated and how many times it has been treated
* Tracker files contain information about sample processing


## Entering health statuses - (<Location>_ColonyData.csv)
 Update health statuses of existing colonies

If a previously tagged colony becomes diseased, record date disease in colony file (healthy until a date is entered)
If previously tagged colony dies, record date mortality in colony file (healthy or diseased until a date is entered)
If disease signs were never observed in dead coral but disease is the assumed cause of death, write unknown in date diseased
If dead coral never displayed disease signs, and it is likely a different cause of death, write NA in date diseased

Add <MonthYear>_Condition, <MonthYear>_Percentage, and Notes_<MonthYear> each sampling trip. 
Condition codes:
* Healthy
* Diseased 
* Diseased_Other = Any disease other than sctld. If you can ID the disease, write in the notes
* Dead 
* CLP = Color loss Paling
* CLB = Color loss bleaching
* DC = Discoloration 
* Not_Visited = colony was not visited on that date. 
If colonies have multiple conditions, comma separate and always use the order above 
**Notes**: 
- We are no longer including TL as a condition. You can record increased old mortality or non-diseased TL in the notes. \
- Even if a colony is assumed dead, write Not_Visited in condition column unless you actually checked on the colony for that date \
- Refer to protocol for assistance determining health statuses https://docs.google.com/document/d/1uF0oCXpHGhzmr21jTfQEbhfTZbGTEc45MjtK-CmH7zs/edit#heading=h.q74g539w5fpz \


Enter the corresponding percentage of colony affected by each condition:
* Only conditions with percentages: CLP, CLB, DC
* Write NA or leave blank for healthy, diseased, dead, or not visited conditions 
* If multiple conditions, be sure to report percentages in the same order as the conditions appear (comma separated), so it's clear what the percent is associated with (ex: "CLP,CLB" - "80%,20%" means 80% CLP and 20% CLB)

Date_InitialTag, Date_DocumentedDisease, and Date_DocumentedMortality are written in MM/DD/YYYY format. Column names are written as MMYYYY (MonthYear).

## Entering new tagged colonies - (<Location>_ColonyData.csv)
Enter new tagged colonies into colony data

Document tagged colony size and location by filling out info for the folowing columns (follow order in spreadsheet):
* Date_InitialTag (MM/DD/YYYY), NewTagNum (tag #. note tag #s are unique within a site but are repeated across sites) & OldTagNum (only applicable for corals tagged in 2019)
* Transect (Transect Code, BEL codes listed below) & TransectNum (T# associated with codes, BEL listed below)
* Species (codes below)
* MaxDiameter (cm), Height (cm), & Size_Class (no longer in use, ignore)
* Meter (meter length (m) along transect where coral is tagged), Meters_90 (length (m) perpendicular to transect line of where coral is tagged), and Direction (L or R of transect line)

Then, follow instructions to enter health condition for initial tagging date    

## Entering new samples - (<Location>_Samples.csv)
Add new samples into sample data files 

CollectionDate & DateSequenced are in MM/DD/YY format, and Month_year is MMYYYY 
- to keep a leading 0 if month is single digit, 
    - when you open excel select "Do not convert" if it prompts you to
    - if it automatically changes it, go to home->numer->'more number formats' from drop down menu->custom: type '000000' into "Type", and apply to the whole column 
- if the other date formats are automatically changed, you can fix this by highting the columns and applying the correct formats by going to home->numer->'more number formats' from drop down menu->date

Health_status describes the sampled tissue. Options are:
* Healthy  
* Diseased_Tissue = apparently healthy tissue on a diseased coral
* Diseased_Margin = collected at disease margin
* Bleached_Tissue = apparently healthy tissue on bleached/paled coral 
* Bleached_Margin = collected from paled/bleached area on coral 
	* can look at condition and percentage info for extent of bleaching/paling on the sampled coral 
* **Follow correct case formatting** 

Sample Type options are:
* Core_Frozen
* Core_EtOH
* Core_RNAlater
* Immune
* Syringe
* Probiotics 
* TEM

If a sample is taken from a non tagged coral, 
* put "AS" (Accidental Sample) in NewTagNum
* provide info on location of sampled coral in the notes 

To create the "Tubelabel_species" column, use the following excel forumla: =CONCAT(A2,"_",B2,"_",C2,"_T",F2,"_",M2,"_",I2)


Sample physical location should note the freezer where the tissue sample is located. When the tissue samples have been completely used, write depleted in this column followed by the location

Extraction physical location should note the freezer where the extracted DNA or RNA is located. When the extracted DNA/RNA is completely used, write depleted in this column. 

When sequenced, write the date that the sequences were received from the sequencer

## Entering Antibiotic Treatment Data 
* When a tagged colony has been treated with antibiotics the treatment should be noted in both SAN_Antibiotictreatment and SAN_ColonyData 
* In the SAN_ColonyData sheet find the colony and place a "Y" in the "Antibiotic_Treatment" column 
* In the SAN_Antibiotictreatment spreadsheet find the treated tagged colony. If never treated with antibiotics before fill out the "Antibiotic_Trearment" column with a "Y". Then put the month and year of the treatment in the mmyyyy format.For example a coral first treated in June 2024 would be recorded uner the "treatment_1" as 062024.
* Subsequent treatments should be recorded in the same fashion. If that same coral was treated again in January 2025, under "treatment_2" you would put 012025.

## General Data Entry Notes
* There should be no spaces in column names or data entries (except for notes). Use underscores instead of spaces if needed. 
* All acronyms should be uppercase and all other entries should be written in Pascal_Snake_Case - all words have first letter capitalized, all words are separated by underscores 
* If OFAV or OANN species cannot be determined, enter ORBI 
* MonthYears are written in MMYYY format, full dates are written in MM/DD/YY formats. 

## Location codes
* SAN=San Andrés Island, Colombia 

### SAN Transect Codes
NIRVANA (T1)
PUNTAPADI (T2)
ROCOSA(T3)
PLAZADETOROS (T4)
ELARBOL (T5)

Make all location and transect codes uppercase

## Species codes 
* SSID - Siderastrea siderea
* PAST - Porites astreoides
* PSTR - Pseudodiploria strigosa
* MCAV - Montastraea cavernosa
* CNAT - Colpophyllia natans
* DLAB - Diploria labyrinthiformis
* MMEA - Meandrina meandrites
* OANN - Orbicella annularis
* OFAV - Orbicella faveolata
* ORBI - Orbicella colony (OFAV/OANN) that cannot be determined to species level. 

