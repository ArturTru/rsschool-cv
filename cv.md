Artur Trushynski

Engineer (2years of experience)
=============================

Contacts
-------- 
Belarus
Minsk

arturius.by@gmail.com

Discord:
Arthur Trushynski (@arturtru)
ART_747#7781

Education 
---------

-BSUIR 2018-2020 - information systems software

-BSPU 2012-2018 - teacher - artist

Experience
----------
School № 64 
Engineer
2020 - till present

OSVOD - Minsk
Rescue Diver
2011 - 2021

My Skills
----------
-C/C++
-C#
-OOP
-WPF
-Js
-SQL


code example
------------
namespace lab1_2019.Controllers
{
    public class ProductController : Controller
    {
        public List<Dish> _dishes;
        List<DishGroup> _dishGroups;
        int _pageSize;
        public ProductController()
        {
            _pageSize = 3;
            SetupData();
        }

        public IActionResult Index(int? group, int pageNo = 1)
        {
            // Поместить список групп во ViewData
            ViewData["Groups"] = _dishGroups;
            // Получить id текущей группы и поместить в TempData
            var currentGroup = 0;
            int.TryParse(HttpContext
            .Request.Query["group"], out currentGroup);
            TempData["CurrentGroup"] = currentGroup;
            var items = _dishes
                .Skip((pageNo - 1) * _pageSize)
                .Take(_pageSize)
                .ToList();
            return View(ListViewModel<Dish>.GetModel(_dishes, pageNo, _pageSize));
        }

        private void SetupData()
        {
            _dishGroups = new List<DishGroup>
            {
                new DishGroup {DishGroupId = 1, GroupName = "Стартеры"},
                new DishGroup {DishGroupId = 2, GroupName = "Салаты"},
                new DishGroup {DishGroupId = 3, GroupName = "Супы"},
                new DishGroup {DishGroupId = 4, GroupName = "Основные блюда"},
                new DishGroup {DishGroupId = 5, GroupName = "Напитки"},
                new DishGroup {DishGroupId = 6, GroupName = "Десерты"}
            };

            _dishes = new List<Dish>
            {
                new Dish
                {
                    DishId = 1, DishName = "Суп-харчо",
                    Description = "Очень острый, невкусный",
                    Calories = 200, DishGroupId = 3, Image = "1.jpg"
                },
                new Dish
                {
                    DishId = 2, DishName = "Борщ",
                    Description = "Много сала, без сметаны",
                    Calories = 330, DishGroupId = 3, Image = "2.jpg"
                },
                new Dish
                {
                    DishId = 3, DishName = "Котлета пожарская",
                    Description = "Хлеб - 80%, Морковь - 20%",
                    Calories = 635, DishGroupId = 4, Image = "3.jpg"
                },
                new Dish
                {
                    DishId = 4, DishName = "Макароны по-флотски",
                    Description = "С охотничьей колбаской",
                    Calories = 524, DishGroupId = 4, Image = "макароны.jpg"
                },
                new Dish
                {
                    DishId = 5, DishName = "Компот",
                    Description = "Быстро растворимый, 2 литра",
                    Calories = 180, DishGroupId = 5, Image = "компот.jpg"
                }
            };
        }
    }
}
-----------------------------------------------------------------------------------