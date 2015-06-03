

 - [Database Design](#database-design)
	 - Member Collection
	 - User Collection
 - [Wireframe](#wireframe-for-addedit-publisher-admin-account)
	 - Super Admin dashboard
	 - Publisher Admin dashboard

###**Database Design:**
<hr/>
####***Member Collection:***

```
1. memberId: {
     type: Number,
     unique: true
   },
2. primaryName: {
     type: String,
     unique: true
   },
3. displayName: String,
4. shortName: {
     type: String,
     unique: true
   },
5. currentSettings: {
     publicAccessReuseLicenses: [String],
     techContact: String,
     businessContact: String,
     licenseContact: String
   },
6. settings: [{
     date: {
       type: Date,
       default: new Date()
     },
     publicAccessReuseLicenses: [String],
     techContact: String,
     businessContact: String,
     licenseContact: String,
     modifiedBy: 
       user: String,
       ipAddress: String
     }
   }],
7. isActive: {
     type: Boolean,
     default: true
  },
8. updatedAt: Date,
9. createdAt: {
     type: Date,
     default: new Date()
   }
```

####***User Collection:***
```
1.  username: {
	  type: String,
      required: true,
      unique: true
   },
2. emailAddress: String,
3. salt: String,
4. hash: String,
5. role: {
      type: String,
      default: 'agency_admin',
      enum: ['super_user', 'agency_admin', 'publisher_admin']
   },
6. agency: {
       type: mongoose.Schema.Types.ObjectId,
       ref: 'Agency'
  },
7. publisher: {
     type: mongoose.Schema.Types.ObjectId,
     ref: 'Member'
  },
8. createdAt: {
     type: Date,
     default: new Date()
  },
9. updatedAt: {
     type: Date,
     default: new Date()
  }
```

### **WireFrame for Add/Edit Publisher Admin Account **
<hr/>

####***Super Admin dashboard***

Super Admin can add publisher account by clicking on "Add Account" button of existing publisher from publisher list table:-

![enter image description here](https://dl.dropboxusercontent.com/s/s4c9jznd4stjkx4/showPublishers.png?dl=0)

After that, add publisher account form(below) will open where super admin can add all the necessary info.

![enter image description here](https://dl.dropboxusercontent.com/s/f0gymikjdtbhdre/add-account.png?dl=0)

If any publisher already have admin account then, super admin can modify publisher admin username and password by clicking on "Update Credential" button from publisher list table and it will open below form:

![enter image description here](https://dl.dropboxusercontent.com/s/ebp36uk39l4yv2v/update-credential.png?dl=0)

####***Publisher Admin dashboard***

Publisher admin can login and modify all information from below form:

![enter image description here](https://dl.dropboxusercontent.com/s/89s2yjitmspj9yl/publisher-home-page.png?dl=0)