# first program using .net
programs using .net
c# model
using System.ComponentModel.DataAnnotations;

namespace RegistrationApp.Models
{
    public class RegisterModel
    {
        [Required]
        public string Name { get; set; }

        [Required]
        [EmailAddress]
        public string Email { get; set; }

        [Required]
        [DataType(DataType.Password)]
        public string Password { get; set; }
    }
}


c# model
using Microsoft.AspNetCore.Mvc;
using RegistrationApp.Models;

namespace RegistrationApp.Controllers
{
    public class AccountController : Controller
    {

        public IActionResult Register()
        {
            return View();
        }

    
        [HttpPost]
        public IActionResult Register(RegisterModel model)
        {
            if (ModelState.IsValid)
            {
                ViewBag.Message = "Registration Successful!";
                return View();
            }

            return View(model);
        }
    }
}

html using asp.net
@model RegistrationApp.Models.RegisterModel

<h2>Registration Page</h2>

<form asp-action="Register" method="post">
    
    <div>
        <label>Name:</label>
        <input asp-for="Name" />
        <span asp-validation-for="Name"></span>
    </div>

    <div>
        <label>Email:</label>
        <input asp-for="Email" />
        <span asp-validation-for="Email"></span>
    </div>

    <div>
        <label>Password:</label>
        <input asp-for="Password" type="password" />
        <span asp-validation-for="Password"></span>
    </div>

    <button type="submit">Register</button>
</form>

@if (ViewBag.Message != null)
{
    <p style="color:green">@ViewBag.Message</p>
}
