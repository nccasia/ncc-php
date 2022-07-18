# Chapter 06: Service and Repository layer in Laravel

Mục tiêu:<br>
_Nắm được về 1 structure khoa học hơn so với MVC nguyên bản của Laravel.<br>
_Hình thành được tư duy về layer trong phát triển phần mềm<br>

## Service layer
_Là một lớp xử lý đặt phía sau Controller. Với nhiệm vụ của Controller được gói gọn trong việc điều hướng và cấu hình dữ liệu lần cuối trước khi trả về, thì phần business tính toán được đẩy hết vào lớp trung gian sau đó là Service.
_Layer này sẽ kết nối với các model và repository. Các hàm trong service được chia nhỏ thành các unit giúp cho việc tái sử dụng code và testing được dễ dàng.

## Repository layer
_Lớp trung gian thay thế việc crud bên trong model.<br>

### Cách triển khai:

_Thiết kế 1 class đặt tên là BaseRepository. Class này nhận vào Eloquent model, và bao gồm các phương thức CRD cơ bản.
```php
use Illuminate\Database\Eloquent\Model;

class BaseRepository
{
    protected Model $model;

    public function __construct(Model $model)
    {
        $this->model = $model;
    }

    public function getModel(): Model
    {
        return $this->model;
    }

    public function getAll(): Collection
    {
        return $this->model->newModelQuery()->get();
    }

    public function findById(int $id)
    {
        return $this->model->newModelQuery()->find($id);
    }

    // ...
}
```

_Viết các repository con cho từng model trong dự án, các repo đó đều mở rộng từ BaseRepo.<br>
Ngoài ra các repo này cần implements các interface tương ứng, nhằm mục đích triển khai theo Dependency Injection

```php
use App\Models\User;

class UserRepository extends BaseRepository implements UserRepositoryInterface
{
    protected User $model;

    // override model of BaseRepo
    public function __construct(User $model)
    {
        $this->model = $model;
    }

    public function getActiveUsers(): Collection
    {
        return $this->newModelQuery()->where('status', Status::Active)->get();
    }

    // ...
}
```

_Binding các implementation với interface trong ServiceProvider
```php
namespace App\Providers

use Illuminate\Support\ServiceProvider;

class RepositoryProvider extends ServiceProvider
{
    public function register()
    {
        // Application
        $this->app->bind(UserRepositoryInterface::class, UserRepository::class);
    }
}
```

_Khai báo provider ở trên trong config\app.php
```php
'providers' => [
    //...

    App\Providers\RepositoryProvider::class,
]
```

_Sau khi hoàn thành các bước trên, sử dụng typehint interface và sau đó Service Container của laravel sẽ tự động resolve ra instance cho chúng ta.
```php
class UserService
{
    private $userRepository;

    public function __construct(UserRepositoryInterface $userRepository)
    {
        $this->userRepository = $userRepository;
    }

    public function updateActiveUsers()
    {
        $activeUsers = $this->userRepository->getActiveUsers();
        // another business logic
        // ...
    }
}
```

### Lưu ý:
_Nếu sau này cần sử dụng implementation khác (ví dụ: query với NoSQL), ta chỉ cần viết 1 UserRepo khác với tên khác đi một chút, rồi binding trong Provider là được.
_Triển khai Dependency Injection có thể áp dụng cả với các Service, nhất là trong cấu trúc DDD.
