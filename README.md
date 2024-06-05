  public async Task<IEnumerable<IdentityError>> Register(Register register)
  {dd
  //this is wring
      ApplicationUser.FirstName = register.FirstName;
      ApplicationUser.LastName = register.LastName;
      ApplicationUser.Email = register.Email;
      ApplicationUser.UserName = register.Email;

      var result = await _userManager.CreateAsync(ApplicationUser, register.Password);

      if (result.Succeeded)
      {
          await _userManager.AddToRoleAsync(ApplicationUser, "Admin");
      }
      return result.Errors;
  }
