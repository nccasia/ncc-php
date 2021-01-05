A repository represents an architectural layer that handles communication between the application and data source.

```php
<?php
namespace App\Repositories\Contracts;

interface ProductRepositoryInterface
{
   public function search($name);

   public function getAllByUser($user_id);

   public function getAllByCategory($category_id);
}
```



```php
<?php
namespace App\Repositories\Eloquent;

use App\Repositories\Contracts\ProductRepositoryInterface;
use App\Entity\Product;

class ProductRepository implements ProductRepositoryInterface
{

   public function search($name)
   {
      return Product::where('title', 'LIKE', '% ' . $name . '%')
         ->get();
   }

   public function getAllByUser($user_id)
   {
      return Product::where('user_id', '=', $user_id)
         ->get();
   }

   public function getAllByCategory($category_id)
   {
      return Product::where('category_id', '=', $category_id)
         ->get();
   }
}
```


```php
<?php
namespace App\Http\Controllers;

use Illuminate\Routing\Controller as BaseController;
use Illuminate\Http\Request;
use App\Repositories\Contracts\ProductRepositoryInterface;
class ProductController extends BaseController
{
   protected $productRepository;

   // $productRepository will call the methods from the
   // class defined above in the service provider
   public function __construct(ProductRepositoryInterface
      $productRepository)
   {
      $this->productRepository = $productRepository;
   }

   public function search(Request $request)
   {
      $name = $request->input('name');
      $products = $this->productRepository->search($name);
      return view('home.index', ['products' => $products]);
   }
}
```