[# backend-standard](https://github.com/antoniopapa/laravel-ambassador

# ใน Laravel เวอร์ชัน 11 มีการเปลี่ยนแปลงบางอย่างที่ควรรู้เกี่ยวกับการตั้งค่าและไฟล์ที่สำคัญ ดังนี้
# ไฟล์ config ที่เคยอยู่ในโฟลเดอร์ config จะถูกซ่อนไว้เพื่อป้องกันการแก้ไขที่ไม่ได้ตั้งใจและเพิ่มความปลอดภัยให้แอปพลิเคชัน. คุณสามารถเผยแพร่และแก้ไขไฟล์เหล่านี้ด้วยคำสั่ง
` php artisan config:publish` 



# ไฟล์ Api:
# ฟล์ api.php ไม่ได้ถูกวางไว้ในโฟลเดอร์ web ค่าเริ่มต้น ใน Laravel 11 คุณต้องใช้คำสั่ง php artisan install:api เพื่อนำเข้าไฟล์เส้นทาง API เพื่อใช้งาน.
 ` php artisan install:api `



# การสร้างโปรเจกต์ Laravel ใหม่

## ขั้นตอนการติดตั้งและตั้งค่า

### 1. ติดตั้ง Composer
Laravel ต้องการ Composer ในการจัดการ dependencies. คุณสามารถติดตั้ง Composer ได้จาก [Composer](https://getcomposer.org/).

### 2. สร้างโปรเจกต์ Laravel
เปิด Terminal หรือ Command Prompt และรันคำสั่งด้านล่างเพื่อสร้างโปรเจกต์ Laravel ใหม่:

```sh
composer create-project --prefer-dist laravel/laravel project-name
```
แทนที่ `project-name` ด้วยชื่อโปรเจกต์ของคุณ

### 3. ตั้งค่า Environment
หลังจากสร้างโปรเจกต์เสร็จแล้ว ให้คุณเข้าไปที่โฟลเดอร์ของโปรเจกต์ด้วยคำสั่ง:

```sh
cd project-name
```

คัดลอกไฟล์ `.env.example` เป็น `.env`:

```sh
cp .env.example .env
```

เปิดไฟล์ `.env` และแก้ไขการตั้งค่าต่าง ๆ เช่น การตั้งค่าฐานข้อมูล:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=sanctum
DB_USERNAME=root
DB_PASSWORD=
```

### 4. สร้าง Application Key
รันคำสั่งนี้เพื่อสร้าง application key สำหรับโปรเจกต์
ซึ่งคีย์นี้สำคัญในการรักษาความปลอดภัยสำหรับการเข้ารหัสข้อมูลในแอปพลิเคชันของคุณ

```sh
php artisan key:generate
```

### 5. ตั้งค่าเว็บเซิร์ฟเวอร์
คุณสามารถใช้ built-in PHP development server เพื่อรันโปรเจกต์ Laravel ของคุณ:

```sh
php artisan serve
```

เปิดเบราว์เซอร์และไปที่ `http://localhost:8000` เพื่อดูโปรเจกต์ของคุณ

 ` php artisan migrate `


## ครั้งแรก api จะไม่มี ให้เราสร้างไฟล์ที่ โฟเดอร์
 ` route/api.php ` 

## เพิ่มคอนฟิกให้รู้จัก ที่ไฟล์ api.php 
` /Users/tcp/Desktop/LannnLaaa/project-sanctum/bootstrap/app.php ` 
 `api: __DIR__.'/../routes/api.php',`

## ------------------------------------------------------------ 
## การใช้ Laravel Sail สำหรับ Docker
## ------------------------------------------------------------ 
### 1. ติดตั้ง Docker Desktop
ดาวน์โหลดและติดตั้ง Docker Desktop จาก [Docker](https://www.docker.com/products/docker-desktop).

### 2. สร้างโปรเจกต์ Laravel ด้วย Sail
ใช้คำสั่งด้านล่างเพื่อสร้างโปรเจกต์ Laravel ใหม่ที่พร้อมใช้ Sail:

```sh
curl -s "https://laravel.build/project-name" | bash
```
แทนที่ `project-name` ด้วยชื่อโปรเจกต์ของคุณ

### 3. เริ่มต้นโปรเจกต์ด้วย Sail
เข้าไปที่โฟลเดอร์โปรเจกต์ของคุณ:

```sh
cd project-name
```

รันโปรเจกต์ด้วย Sail:

```sh
./vendor/bin/sail up
```

./vendor/bin/sail up

## ------------------------------------------------------------ 
## ------------------------------------------------------------ 

เปิดเบราว์เซอร์และไปที่ `http://localhost` เพื่อดูโปรเจกต์ของคุณ

# # # # # # # # # # # # # # # # # # # # # # # # # # # # 


# Routing Customization การกำหนด routing ขึ้นมาเอง เช่น เดิมใช้ api เพิ่มเป็น myapi
`http://127.0.0.1:8000/api/getdata`
เป็น
`http://127.0.0.1:8000/myapi/getdata`

# ไปคอนฟิกที่ไฟล์ 
`/Users/tcp/Desktop/LannnLaaa/project-sanctum/bootstrap/app.php`
  `health: '/up',`  <--- เพิ่มต่อจากนี้
  `      then: function () {`
  `          Route::namespace('Admin')`
  `              ->prefix('admin') //<- here`
  `              ->name('admin.')`
  `              ->group(base_path('routes/admin.php'));`
  `      },`
  # use Illuminate\Support\Facades\Route;
  # จากนั้นไปกำหนด route ที่ไฟล์ 
 ` /Users/tcp/Desktop/LannnLaaa/project-sanctum/routes/admin.php`

 `  <?php `
 `       use App\Http\Controllers\Api\MyApiController; `
 `       use Illuminate\Support\Facades\Route;  `
 `       Route::get('/', function () {   `
 `           return response()->json(['message' => 'This is a custom endpoint']); `
 `       });`
  # เท่านี้เราสามารถเรียก url `http://127.0.0.1:8000/myapi/getdata`


# # # # # # # # # # # # # # # # # # # # # # # # # # # # 


# -------------------- Lesson 6 --------------------
 `   php artisan make:Controller AuthController `
 ./vendor/bin/sail artisan make:controller AuthController


# กรณีไม่มี file route.php  ให้สร้างขึ้นเอง ด้วยคำสั่ง
` touch routes/route.php `
#  เพิ่มโค้ด

`    <?php  `
`    use Illuminate\Support\Facades\Route;    `

`    Route::get('/', function () {            `
`        return view('welcome'); `
`    }); `

`    Route::get('/about', function () { `
`        return 'About Page'; `
`    }); `


# สร้าง basic route 
<!-- Route::get('/register', [AuthController::class, 'register']); -->
# ปรับเป็น

<!-- Route::prefix('admin')->group(function () {
 Route::post('register', [AuthController::class, 'register']);  
}); -->

# Controller
  <!-- <?php

  namespace App\Http\Controllers;

  use Illuminate\Http\Response;

  class AuthController extends Controller
  {
      public function register()
      {
          // You can replace this with the actual user data if available
          $user = ['message' => 'Hello'];

          return response()->json($user, Response::HTTP_CREATED);
      }
  } -->

# -----------------------------------------------------------  
# -------------------- Lesson 7 Register --------------------
# สร้างไฟล์คลาส Request ใหม่ที่ใช้สำหรับการตรวจสอบข้อมูลที่เข้ามาในรูปแบบของ HTTP Request โดยเฉพาะในกรณีนี้คือการลงทะเบียนผู้ใช้. การสร้าง Request ที่เฉพาะเจาะจงเช่นนี้ช่วยให้คุณได้รับประสิทธิภาพในการตรวจสอบและจัดการข้อมูลที่ส่งผ่าน HTTP อย่างมีประสิทธิภาพขึ้น

` php artisan make:request RegisterRequest `

# กำหนด ฟังก์ชัน authorize() ในคลาส Request ของ Laravel เป็นฟังก์ชันที่ใช้ในการกำหนดเงื่อนไขว่าคำขอที่เข้ามาสามารถอนุญาตให้ดำเนินการต่อหรือไม่ การกำหนด return true; ใน authorize() จะทำให้ทุกคำขอสามารถผ่านการตรวจสอบได้โดยไม่มีการจำกัดเงื่อนไขอื่น ๆ ที่ต้องพิจารณาก่อนการอนุญาตให้ผ่านไปขั้นตอนถัดไป

# กำหนด  /app/Http/Requests/RegisterRequest.php 
   <!-- public function authorize(): bool
    {
        return true;
    }
   
# กำหนดว่าต้องการ field อะไร
    public function rules(): array
    {
        return [
            'first_name' => 'required',
            'last_name' => 'required',
            'email' => 'required|email',
            'password' => 'required',
            'password_confirm' => 'required|same:password',
        ];
    }    

 } -->

#  ที่ไฟล์ AuthController  ปรับ parameter register function ->  RegisterRequest $request
<!-- 
class AuthController extends Controller
{
    public function register(RegisterRequest $request)
    {
        return 'this is a register controller';
    }
} -->
 # ทดสอบการทำงานของคลาส RegisterRequest  ว่าทำงานได้ใหม
 # http://localhost:8000/api/admin/register  จะไม่แสดงข้อความทืั่ต้องการ 
 #  ให้ไปที่ postman ปรับ tab header เพิ่ม
 ` Accept  application/json `
 
 # ข้อความที่ได้จะผ่านคลาส Request  ก่อน authorize true
 <!-- 
 {
    "message": "The first name field is required. (and 4 more errors)",
    "errors": {
        "first_name": [
            "The first name field is required."
        ],
        "last_name": [
            "The last name field is required."
        ],
        "email": [
            "The email field is required."
        ],
        "password": [
            "The password field is required."
        ],
        "password_confirm": [
            "The password confirm field is required."
        ]
    }
} -->

# open postman   go to tab body -> raw -> json 
# using method post  http://localhost/api/admin/register
<!-- {
    "first_name": "jhondoes",
    "last_name": "brain",
    "email": "jhondoe@email.com",
    "password": "a",
    "password_confirm": "a"
} -->
# ผลลัพธ์จาก postman 
` this is a register controller `


# สร้าง helper file จะได้ file _ide_helper.php 
# จะใช้ประโยชน์ในการ Hash
 ` composer require --dev barryvdh/laravel-ide-helper  `

# คำสั่ง php artisan ide:generate ใน Laravel ใช้สร้างไฟล์ .phpstorm.meta.php ซึ่งเป็นไฟล์ที่ใช้ในการจับคู่กับ IDE เช่น PhpStorm เพื่อปรับปรุงความเข้าใจของ IDE เกี่ยวกับโค้ด Laravel ของคุณ ไฟล์นี้ช่วยให้ IDE สามารถเสนอคำแนะนำในการเขียนโค้ดได้แม่นยำขึ้น รวมถึงช่วยในการสร้างรหัสอัตโนมัติและความสามารถในการนำทางไปยังคลาสและเมทอดที่ถูกสร้างขึ้นจากการเรียกใช้ในโค้ดของคุณ
  ` php artisan ide:generate   `


# คำสั่ง php artisan ide:models ใน Laravel จะสร้างคำสั่งสำหรับสร้างไฟล์ PHPDoc สำหรับแบบจำลอง (Models) ทั้งหมดที่อยู่ในโปรเจ็กต์ Laravel ของคุณ ซึ่งมีไว้เพื่อช่วยในการเขียนโค้ดและเพิ่มความชัดเจนในการเข้าใจโครงสร้างข้อมูลของแต่ละแบบจำลอง คำสั่งนี้มักจะถูกใช้งานในการพัฒนาและเพิ่มประสิทธิภาพในการทำงานกับฐานข้อมูลของคุณ
# จะได้ไฟล์  app/Models/User.php 

  ` php artisan ide:models  `

# ปรับโค็ด app/Models/User.php ไม่ต้อง return password
<!-- 
class User extends Authenticatable
{
    use HasApiTokens, Notifiable;
    protected $hidden = [
        'password'
    ];
} -->


 # ปรับ AuthController

<!--      
     public function register(RegisterRequest $request)
    {
        $user = User::create(
            $request->only('first_name', 'last_name', 'email')
                + [
                    'password' => \Hash::make($request->input('password')),
                    'is_admin' => $request->path() === 'api/admin/register' ? 1 : 0
                ]
        );

        return response($user, Response::HTTP_CREATED);
    } -->


# ไปที่ /app/Models/User.php เพิ่ม $guarded = [];
<!-- 
    สามารถใช้ $guarded = []; ในโมเดลของ Laravel เพื่อเปิดให้ทุกฟิลด์ในโมเดลนั้นสามารถรับค่าจาก  
    Mass Assignment  (การกำหนดค่าได้หลายค่าพร้อมกัน)  ได้ โดยไม่จำกัดฟิลด์ใด ๆ นั่นหมายความว่าคุณยินยอมให้ข้อมูลสามารถส่งผ่านแบบ
     Mass Assignment ได้ทั้งหมด ซึ่งเป็นวิธีที่สะดวกในการจัดการข้อมูลและลดความซับซ้อนในการกำหนดค่าแต่ละฟิลด์อย่างเดียว -->


# ทดสอบใน postman 
<!-- 
http://localhost:8000/api/admin/register
tab  body -> raw ใส่ลงไป 
{
    "first_name": "John",
    "last_name": "Doe",
    "email": "john.doe@example.com",
    "password": "password",
    "password_confirm": "password"
} -->

# -----------------------------------------------------------  
# -------------------- Lesson 8 Login with sanctum ----------
# สร้าง route and controller login 
<!-- 
 route 
  Route::post('login', [AuthController::class, 'login']);

 controller 

  public function login(Request $request)
    {
        if (!\Auth::attempt($request->only('email', 'password'))) {
            return response([
                'error' => 'invalid credentials'
            ], Response::HTTP_UNAUTHORIZED);
        }

        $user = \Auth::user();

        $adminLogin = $request->path() === 'api/admin/login';

        if ($adminLogin && !$user->is_admin) {
            return response([
                'error' => 'Access Denied!'
            ], Response::HTTP_UNAUTHORIZED);
        }

        $scope = $adminLogin ? 'admin' : 'ambassador';
        $jwt = $user->createToken('token', [$scope])->plainTextToken;

        $cookie = cookie('jwt', $jwt, 60 * 24); // 1 day
        return response([
            'message' => 'success', 
            'jwt' => $jwt  // เพิ่ม JWT เข้าไปใน response
        ])->withCookie($cookie);
    } -->

# ใช้งาน jwt ผ่าน  sanctum
    composer require laravel/sanctum
    php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"

# ไปที่  app/Models/User.php 
# use on top  comment Passport  use Laravel\Passport\HasApiTokens;
    use Laravel\Sanctum\HasApiTokens;

# use in class 
    use HasFactory, Notifiable,HasApiTokens;

# ไปที่ /config/cors.php
  `   'supports_credentials' => true,  ` 
<!-- 
     การตั้งค่า 'supports_credentials' => true ใน Laravel Sanctum หมายถึงการอนุญาตให้แอปพลิเคชันของคุณส่งคำขอ
     API พร้อมกับข้อมูลการขออนุญาต (credentials) ที่เป็น HTTP headers ไปยังแอปพลิเคชันของคุณ 
     โดยเฉพาะอย่างยิ่งเมื่อคุณใช้ cookies เพื่อการยืนยันตัวตนบนแอปพลิเคชันของคุณ 
     นั่นหมายความว่าคุณสามารถใช้งานการตรวจสอบสิทธิ์โดยตรงผ่าน cookies ในการส่งคำขอ 
     API ของคุณได้โดยไม่ต้องมีการใช้ Bearer Tokens หรือการตั้งค่าอื่น ๆ ที่ซับซ้อนมาก่อน
      -->

# ----------------------------------------------- 
# Lesson 9 Authentication User ------------------

# สร้าง route and controller

<!-- 

Route::middleware(['auth:sanctum']): 
Middleware auth:sanctum จะทำหน้าที่ตรวจสอบการรับรองตัวตนของผู้ใช้ด้วย
 Sanctum ก่อนที่จะให้เข้าถึง Route ที่กำหนด
Route::get('user', [AuthController::class, 'user']): เมื่อผู้ใช้เข้าถึง endpoint /user ด้วย HTTP GET request จะมีการเรียก Controller method user ที่อยู่ใน AuthController
ดังนั้นเมื่อผู้ใช้พยายามเข้าถึง /user จะต้องมีการตรวจสอบว่าผู้ใช้เข้าระบบแล้วด้วย Sanctum ถ้าไม่ผ่านการตรวจสอบจะไม่สามารถเข้าถึงได้

 Route::middleware(['auth:sanctum'])->group(function () {
        Route::get('user', [AuthController::class, 'user']);
    });

    public function user(Request $request)
    {
        return  $request->user();

        // return new UserResource($user);
    }


 -->

 # postman
 method get
   ` http://localhost:8000/api/admin/user  `
 # ที่แทป header  เพิื่ม
   `Accept application/json  `
 # กด send 
  {
      "message": "Unauthenticated."
  }
# เป็นเพราะว่า sanctum ต้องการ header Request ที่เป็น  headerAuthorization Bearer  
# ที่แทป header เพิื่ม
   `  Authorization Bearer  ` 
# ผลลัพธ์ทีได้

<!-- {
    "id": 3,
    "first_name": "John",
    "last_name": "Doe",
    "email": "john.doe@example.com",
    "is_admin": 1,
    "created_at": "2024-07-15T04:51:29.000000Z",
    "updated_at": "2024-07-15T04:51:29.000000Z"
} -->

# กำหนด jwt Bearer
  `  php artisan make:middleware Authenticate  ` 










# การใช้งาน laravel download form git 
❯ composer install
Installing dependencies from lock file (including require-dev)
Verifying lock file contents can be installed on current platform.
Your lock file does not contain a compatible set of packages. Please run composer update.

  Problem 1
    - phpspec/prophecy is locked to version 1.12.2 and an update of this package was not requested.
    - phpspec/prophecy 1.12.2 requires php ^7.2 || ~8.0, <8.1 -> your php version (8.3.8) does not satisfy that requirement.
  Problem 2
    - phpspec/prophecy 1.12.2 requires php ^7.2 || ~8.0, <8.1 -> your php version (8.3.8) does not satisfy that requirement.
    - phpunit/phpunit 9.5.2 requires phpspec/prophecy ^1.12.1 -> satisfiable by phpspec/prophecy[1.12.2].
    - phpunit/phpunit is locked to version 9.5.2 and an update of this package was not requested. 


#  ติดตั้ง Laravel Basic Command 
php artisan migrate
php artisan make:Controller xxx
php artisan make:Request RegisterRequest

php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear
composer dump-autoload
php artisan optimize

# สร้าง basic function
php artisan ide:models  
composer require --dev barryvdh/laravel-ide-helper

# # # # # # # # # # # # # # # # # # # # # # # # # # # # 
#  sanctum
composer require laravel/sanctum

php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"

php artisan migrate


# docker basic command 

docker compose up -d

 docker compose ps

docker compose down

docker exec -it <ชื่อ-container-php> bash
composer install

# # # # # # # # # # # # # # # # # # # # # # # # # # # # 
#    auto command ~/.zshrc 
  ` alias sail='sh $([ -f sail ] && echo sail || echo vendor/bin/sail)'  `

# # # # # # # # # # # # # # # # # # # # # # # # # # # # 
#    sail basic command
 sail up -d
 sail down
 sail artisan migrate
 log
 ps


mikung-invitrace
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


)
