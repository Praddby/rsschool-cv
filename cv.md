#### My name is Yury Bialou.

#### Contact Info
* I am live in *Minsk*
* My e-mail: *Pradd.by@gmail.com*
* My skype: *Pradd.*

#### Summary 
* My goal is to start a career **as a full-time web developer**.
* There is little experience in layout and development of simple site functionality.

#### Skills 
* I have a little programming experience in **PHP / HTML / CSS / JavaScript / SQL / Java**.
* Worked with databases like **MySQL / MongoDB**.

#### Code examples 

```javascript
import Bus from '../Bus.js';
import ApiUser from '../../api/users.js';
import ApiPagination from '../../api/pagination.js';
export default {
  data(){
    return{
      pagination: {},
      users: {},
      user_role: {},
      isUser: false,
      showEdite: false,
      roles: {},
      selectedRole: null,
      errors: null,
      modal: {}
    }
  },
  created() {
    ApiUser.get().then(data => {
      this.pagination = data.data;
      this.users = data.data.data;
      this.roles = data.role;
    });
  },
  methods: {
    nextPageUrl() {
      if (this.pagination.current_page != this.pagination.last_page) {
        let params = {
          path: this.pagination
        };
        ApiPagination.next(params).then(data => {
          this.pagination = data.data;
          this.users = data.data.data;
        });
      }
    },
    prevPageUrl() {
      if (this.pagination.current_page != 1) {
        let params = {
          path: this.pagination
        };
        ApiPagination.prev(params).then(data => {
          this.pagination = data.data;
          this.users = data.data.data;
        });
      }
    },
    PageUrl(pageNo) {
      if (this.pagination.current_page != pageNo) {
        let params = {
          path: this.pagination,
          pageNo
        };
        ApiPagination.page(params).then(data => {
          this.pagination = data.data;
          this.users = data.data.data;
        });
      }
    },
    showUser(id){
      ApiUser.show(id)
        .then( (data) => {
          this.errors = null;
          this.user_role = data;
          this.isUser = true;
        }).catch( (error) => {
          this.errors = [error.response.data.message];
        });
    },
    showTableUsers(){
      this.isUser = false;
    },
    showEditeRoleUser(id){
      if ( this.showEdite == id )
        this.showEdite = false;
      else
        this.showEdite = id;
    },
    destroyUserRole(user){
      ApiUser.deleteRole(user.id)
        .then( (data) => {
          this.errors = null;
          user.role = null;
        }).catch( (error) => {
          this.errors = [error.response.data.message];
        });
    },
    changeRole(user){
      let params = {
        roleId: this.selectedRole.id,
        userId: user.id
      };
      ApiUser.changeRole(params)
        .then( (data) => {
          this.errors = null;
          user.role = this.selectedRole;
          this.showEdite = false;
          this.selectedRole = null;
        }).catch( (error) => {
          this.errors =  error.response.data.errors.roleId;
        });
    },
  }
};
```

#### Experience 
__Work experience__ 
  - January 2019 - present
    - backend programmer in Google
 
  - October 2017 - December 2018
    - Bank, programmer
      - Executable functions:
        * development of the server part
        * testing internal programs

#### Education 
- I have a higher education and graduated from Belgut in 2008. 
- In the period from November 2016 to February 2017, he was trained in "Super Courses" in the specialty "development of WEB-oriented applications".

#### English 
- My English level is Pre-Intermediate
