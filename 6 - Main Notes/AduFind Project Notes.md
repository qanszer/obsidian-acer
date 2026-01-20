
2025-12-07  21:57

Tags: [[School]] [[Database]] [[SQL]] [[Coding]]

---

# AduFind Project Notes


### Live Address Link

http://192.168.0.22:5501/index.html


### ERD Context

FoundItems Table
1. Required (NOT NULL constraint)
	- ItemName
	- Description
	- Category (add ng none of the above na category option)
	- DateFound
	- TimeFound
	- ImageURL (ppicturan ng nakahanap)
2. Optional
	- FinderName
	- FinderEmail
3. Hidden (di kasama sa web form; staff mag iinput sa attribute na to)
	- Status

Claims Table
1. Required (NOT NULL constraint)
	- ClaimerFirstName
	- ClaimerLastName
	- ClaimerEmail
	- ItemName
	- ItemCategory
	- ItemDescription
	- DateLost
	- VerificationMethod
	- VerificationDetails
2. Optional
	- ImageFile
3. Hidden (di kasama sa web form; staff mag iinput sa attribute na to)
	- ClaimDate

PlaceFound Table
1. Required (NOT NULL constraint)
	- BuildingName
2. Optional
	- RoomNumber
	- FloorLevel
3. Hidden (di kasama sa web form; staff mag iinput sa attribute na to)
	- StorageBinCode

StaffUsers Table
1. Required (NOT NULL constraint)
	- all








---

## References