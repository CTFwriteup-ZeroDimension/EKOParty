# F#CK (reverse 50)
It's a .net assembly. Use dotPeek to decompile it.  
Find the Program class under root namespace.  
``` c#
// Decompiled with JetBrains decompiler
// Type: Program
// Assembly: FlagGenerator, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null
// MVID: 580A3D8A-2E94-AAA8-A745-03838A3D0A58
// Assembly location: C:\Ralph\CTF\eko\reverse_50\FlagGenerator.exe

using Microsoft.FSharp.Core;
using System;
using System.Globalization;
using System.IO;

[CompilationMapping]
public static class Program
{
  public static string get_flag(string str)
  {
    int[] combiningCharacters = StringInfo.ParseCombiningCharacters(str);
    int length = combiningCharacters.Length;
    FSharpFunc<int, string> fsharpFunc = (FSharpFunc<int, string>) new Program.teArr\u00409(str, combiningCharacters);
    if (length < 0)
      Operators.Raise<Unit>((Exception) new ArgumentException(LanguagePrimitives.ErrorStrings.get_InputMustBeNonNegativeString(), "count"));
    string[] strArray1 = new string[length];
    int index = 0;
    int num = length - 1;
    if (num >= index)
    {
      do
      {
        strArray1[index] = fsharpFunc.Invoke(index);
        ++index;
      }
      while (index != num + 1);
    }
    string[] strArray2 = strArray1;
    Array.Reverse((Array) strArray2);
    return string.Join("", strArray2);
  }

  [EntryPoint]
  public static int main(string[] argv)
  {
    if (argv.Length != 1)
    {
      ExtraTopLevelOperators.PrintFormatLine<Unit>((PrintfFormat<M0, TextWriter, Unit, Unit>) new PrintfFormat<Unit, TextWriter, Unit, Unit, Unit>("Usage: FlagGenerator.exe <FLAG>"));
    }
    else
    {
      string flag = Program.get_flag("t#hs_siht_kc#f");
      if (string.Equals(flag, argv[0]))
        ((FSharpFunc<string, Unit>) ExtraTopLevelOperators.PrintFormatLine<FSharpFunc<string, Unit>>((PrintfFormat<M0, TextWriter, Unit, Unit>) new PrintfFormat<FSharpFunc<string, Unit>, TextWriter, Unit, Unit, string>("EKO{%s}"))).Invoke(flag);
      else
        ExtraTopLevelOperators.PrintFormatLine<Unit>((PrintfFormat<M0, TextWriter, Unit, Unit>) new PrintfFormat<Unit, TextWriter, Unit, Unit, Unit>("BAD ANSWER"));
    }
    return 0;
  }

  [Serializable]
  internal class teArr\u00409 : FSharpFunc<int, string>
  {
    public string str;
    public int[] ccIndices;

    internal teArr\u00409(string str, int[] ccIndices)
    {
      this.\u002Ector();
      this.str = str;
      this.ccIndices = ccIndices;
    }

    public virtual string Invoke(int i)
    {
      if (i == this.ccIndices.Length - 1)
        return this.str.Substring(i);
      int ccIndex = this.ccIndices[i];
      return this.str.Substring(ccIndex, this.ccIndices[i + 1] - ccIndex);
    }
  }
}
```  
The flag is the result of some operations on "t#hs_siht_kc#f", and the function seems to reverse the string.  
The flag is EKO{f#ck_this_sh#t}.

