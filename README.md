# User

[![Join the chat at https://gitter.im/user/Lobby](https://badges.gitter.im/user/Lobby.svg)](https://gitter.im/user/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/bantenprov/user/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/bantenprov/user/?branch=master)
[![Build Status](https://scrutinizer-ci.com/g/bantenprov/user/badges/build.png?b=master)](https://scrutinizer-ci.com/g/bantenprov/user/build-status/master)
[![Latest Stable Version](https://poser.pugx.org/bantenprov/user/v/stable)](https://packagist.org/packages/bantenprov/user)
[![Total Downloads](https://poser.pugx.org/bantenprov/user/downloads)](https://packagist.org/packages/bantenprov/user)
[![Latest Unstable Version](https://poser.pugx.org/bantenprov/user/v/unstable)](https://packagist.org/packages/bantenprov/user)
[![License](https://poser.pugx.org/bantenprov/user/license)](https://packagist.org/packages/bantenprov/user)
[![Monthly Downloads](https://poser.pugx.org/bantenprov/user/d/monthly)](https://packagist.org/packages/bantenprov/user)
[![Daily Downloads](https://poser.pugx.org/bantenprov/user/d/daily)](https://packagist.org/packages/bantenprov/user)


# User
User

### Install via composer

- Development snapshot

```bash
$ composer require bantenprov/user:dev-master
```

- Latest release:

### Download via github

```bash
$ git clone https://github.com/bantenprov/user.git
```

#### Edit `config/app.php` :

```php
'providers' => [

    /*
    * Laravel Framework Service Providers...
    */
    Illuminate\Auth\AuthServiceProvider::class,
    Illuminate\Broadcasting\BroadcastServiceProvider::class,
    Illuminate\Bus\BusServiceProvider::class,
    Illuminate\Cache\CacheServiceProvider::class,
    Illuminate\Foundation\Providers\ConsoleSupportServiceProvider::class,
    Illuminate\Cookie\CookieServiceProvider::class,
    //....
    Bantenprov\User\UserServiceProvider::class,
```

#### Lakukan migrate :

```bash
$ php artisan migrate
```

#### Publish database seeder :

```bash
$ php artisan vendor:publish --tag=user-seeds

```

#### Lakukan auto dump :

```bash
$ composer dump-autoload
```

#### Lakukan seeding :

```bash
$ php artisan db:seed --class=BantenprovUserSeeder
```

#### Lakukan publish component vue :

```bash
$ php artisan vendor:publish --tag=user-assets
$ php artisan vendor:publish --tag=user-public
```
#### Tambahkan route di dalam file : `resources/assets/js/routes.js` :

```javascript
{
    path: '/dashboard',
    redirect: '/dashboard/home',
    component: layout('Default'),
    children: [
        //== ...
       {
        path: '/dashboard/user',
        components: {
            main: resolve => require(['./components/views/bantenprov/user/DashboardUser.vue'], resolve),
            navbar: resolve => require(['./components/Navbar.vue'], resolve),
            sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
        },
        meta: {
            title: "User"
        }
      }
        //== ...
    ]
},
```

```javascript
{
    path: '/admin',
    redirect: '/admin/dashboard/home',
    component: layout('Default'),
    children: [
        //== ...
        {
            path: '/admin/user',
            components: {
                main: resolve => require(['./components/bantenprov/user/User.index.vue'], resolve),
                navbar: resolve => require(['./components/Navbar.vue'], resolve),
                sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
            },
            meta: {
                title: "User"
            }
        },
        {
            path: '/admin/user/create',
            components: {
                main: resolve => require(['./components/bantenprov/user/User.add.vue'], resolve),
                navbar: resolve => require(['./components/Navbar.vue'], resolve),
                sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
            },
            meta: {
                title: "User"
            }
        },
        {
            path: '/admin/user/:id',
            components: {
                main: resolve => require(['./components/bantenprov/user/User.show.vue'], resolve),
                navbar: resolve => require(['./components/Navbar.vue'], resolve),
                sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
            },
            meta: {
                title: "User"
            }
        },
        {
            path: '/admin/user/:id/edit',
            components: {
                main: resolve => require(['./components/bantenprov/user/User.edit.vue'], resolve),
                navbar: resolve => require(['./components/Navbar.vue'], resolve),
                sidebar: resolve => require(['./components/Sidebar.vue'], resolve)
            },
            meta: {
                title: "User"
            }
        },
        //== ...
    ]
},
```
#### Edit menu `resources/assets/js/menu.js`

```javascript
{
    name: 'Dashboard',
    icon: 'fa fa-dashboard',
    childType: 'collapse',
    childItem: [
        //== ...
        {
          name: 'User',
          link: '/dashboard/user',
          icon: 'fa fa-angle-double-right'
      }
        //== ...
    ]
},
```

```javascript
{
    name: 'Admin',
    icon: 'fa fa-lock',
    childType: 'collapse',
    childItem: [
        //== ...
        {
            name: 'User',
            link: '/admin/user',
            icon: 'fa fa-angle-double-right'
          }
        //== ...
    ]
},
```

#### Tambahkan components `resources/assets/js/components.js` :

```javascript

//== Example Vuetable

import User from './components/bantenprov/user/User.chart.vue';
Vue.component('echarts-user', User);

import UserKota from './components/bantenprov/user/UserKota.chart.vue';
Vue.component('echarts-dpp-bank-dinia-kota', UserKota);

import UserTahun from './components/bantenprov/user/UserTahun.chart.vue';
Vue.component('echarts-dpp-bank-dinia-tahun', UserTahun);

import UserAdminShow from './components/bantenprov/user/UserAdmin.show.vue';
Vue.component('admin-view-user-tahun', UserAdminShow);

//== Echarts User

import UserBar01 from './components/views/bantenprov/user/UserBar01.vue';
Vue.component('user-bar-01', UserBar01);

import UserBar02 from './components/views/bantenprov/user/UserBar02.vue';
Vue.component('user-bar-02', UserBar02);

//== mini bar charts
import UserBar03 from './components/views/bantenprov/user/UserBar03.vue';
Vue.component('user-bar-03', UserBar03);

import UserPie01 from './components/views/bantenprov/user/UserPie01.vue';
Vue.component('user-pie-01', UserPie01);

import UserPie02 from './components/views/bantenprov/user/UserPie02.vue';
Vue.component('user-pie-02', UserPie02);

//== mini pie charts
import UserPie03 from './components/views/bantenprov/user/UserPie03.vue';
Vue.component('user-pie-03', UserPie03);
