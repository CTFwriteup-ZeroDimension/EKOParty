# RrEeGgEeXx (reverse 75)
It's another .net assembly. Use dotPeek to decompile it.  
```
// Decompiled with JetBrains decompiler
// Type: RegexAuth.Program
// Assembly: RegexAuth, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null
// MVID: 4F44B0EC-6D3A-46C8-B7F8-78E8F4C6A368
// Assembly location: C:\Ralph\CTF\eko\reverse_75\RegexAuth.exe

using System;
using System.Text.RegularExpressions;

namespace RegexAuth
{
  internal class Program
  {
    private static bool check_regex(string regex, string input)
    {
      return new Regex(regex, RegexOptions.None).Match(input).Success;
    }

    private static void Main(string[] args)
    {
      Console.WriteLine("EKO AUTH CHECKER");
      Console.WriteLine("----------------");
      Console.Write("Password: ");
      string input = Console.ReadLine();
      if (Program.check_regex("^.{40}$", input) && Program.check_regex("\\w{3}\\{.*\\}", input) && (Program.check_regex("_s.*e_", input) && Program.check_regex("\\{o{2}O{2}o{2}", input)) && (Program.check_regex("O{2}o{2}O{2}\\}", input) && Program.check_regex("sup3r_r3g3x_challenge", input)))
        Console.WriteLine("Welcome master");
      else
        Console.WriteLine("IMPOSTOR");
    }
  }
}
```
We can see the conditions are :
1. It's a string whose length is 40.
2. It starts with three word, follows a "{" and ends with "}".
3. It contains "_s" and then after some characters there's "e_".
4. The characters after "{" are ooOOoo.
5. The characters before "}" are OOooOO.
5. It contains "sup3r_r3g3x_challenge".

We can get the flag:  
EKO{ooOOoo_sup3r_r3g3x_challenge_OOooOO}
