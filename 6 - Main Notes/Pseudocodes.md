
2026-04-12  03:17 pm

Tags: [[Coding]], [[Tracking]]

---
# Pseudocodes

This is a list of my pseudocode attempts when I code.

### OOP Midterm Project Activity - Warehouse System
Date: 4/12/26
Language: Java

**ATTEMPT 1** - Fail

```java
public static void main(String[] args) {
		
        chooseRole
        loginOrLogout
        
        prompt ("select an option 1-9")
        
        // option 1 - update password
        prompt ("choose user 1-6 to change password")
        prompt ("enter new password")
        prompt ("confirm new password")
        
        // option 2 - inactivate user
        
    }
    
    public class Technicalities {
        
        method catchErrorInput
		    while storedInfo != inputtedInfo
			prompt ("wrong input! please try again")
        
    }
    
    public class CommonActions {
        
        method chooseRole {
            prompt (select a user role (
				press 1 for admin, 
				2 warehouse, 
				3 user
			))
			
			switch {
				case 1: AdminRole
				case 2: WarehouseRole
				case 3: UserRole
			}
		}
        
        method loginOrLogout {
             prompt (enter username)
             catchErrorInput(username)
             prompt (enter password)
             catchErrorInput(password)
        }
        
        method displayProducts {
             print (class products)
        }
    }
    
    public class AdminRole {
	    LinkedList<AdminAccount> adminAccountsList;
	    LinkedList<AdminAccount> inactiveAdminAccountsList;
	    LinkedList<> allUsers = new LinkedList<>();
	    LinkedList<> allInactiveUsers = new LinkedList<>();
		
		allUsers.append(adminAccountsList);
		allUsers.append(WarehouseRole.warehouseAccountsList);
		allUsers.append(UserRole.userAccountsList);
	    
	    method verifyUser (userInput) {
		    boolean result = false;
		    for (int x = 0; x < adminAccountsList.length; x++) {
			    for (int y = 0; y < adminAccountsList[x].length; y++) {
				    String user = adminAccountsList[x];
				    
				    if (user.equals("userInput")) {
					    result = true;
				    }
			    }
		    }
		    return result;
	    }
        
        method chooseAdminOptions {
	        print (options 1-9)
	        switch {
		        case 1: updatePassword
		        case 2: inactivateUser
		        case 3: addUser
		        case 4: displayAllUsers
		        case 5: displayInactiveUsers
		        case 6: displayActiveUsers
		        case 7: displayProducts
		        case 8: displayOrders
		        case 9: logout
	        }
        }
        
        method updatePassword {
            prompt (choose user to change password)
            prompt (input adminPassword)
                if (inputtedPassword == adminPassword)
                    input (newPassword)
                    if (verifyInput(newPassword) == true)
                         adminPassword = newPassword
                    else
                         chooseAdminOptions
                else
                     print (wrong password)
                     prompt (press 1 updatePassword, 2 chooseAdminOptions)
            print (password change successful!)
        }
        
        method verifyInput {
            input (firstInput)
            input (secondInput)
            if (firstInput == secondInput)
                 return true
            else 
                 print (wrong input)
                 return false
        }
        
		method inactivateUser {
			
		}
		
		method addUser {
			
		}
		
		method displayAllUsers {
			print (allUsers)
		}
    }
    
    public class AdminAccount {
	    String adminId;
        String adminName;
        String adminPassword;
    }
    
    public class WarehouseAccount {
	    String warehouseId;
	    String warehouseName;
	    String warehousePassword;
    }
    
    public class UserAccount {
	    String userId;
	    String userName;
	    String userPassword;
    }
	
	public class Product {
		String productId;
		String productName;
		String productQty;
		boolean isActive;
		String productDate;
		String productCreatedBy;
	}
	
	public class Order {
		String orderName;
		String orderQty;
	}
```


**ATTEMPT 2**

All classes needed
- User
- Users
- AdminChoices
- WarehouseChoices
- UserChoices
- Product
- Products

```java
public static void main {
	
}

class User {
	String userId, userName, userPassword;
}

class Users {
	
}

class AdminChoices {
	
}

class WarehouseChoices {
	
}

class UserChoices {
	
}

class Product {
	
}

class Products {
	
}
```


---


