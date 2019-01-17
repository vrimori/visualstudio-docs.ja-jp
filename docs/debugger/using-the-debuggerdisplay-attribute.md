---
title: DebuggerDisplay 属性の使用 |Microsoft Docs
ms.date: 01/09/2019
ms.topic: conceptual
helpviewer_keywords:
- attributes, debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecbbad832ad206a0a8192d57d2642bc68a8e3902
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54228059"
---
# <a name="using-the-debuggerdisplay-attribute-c-visual-basic-ccli"></a>DebuggerDisplay 属性を使用して (C#、Visual Basic の場合、C +/cli CLI)
<xref:System.Diagnostics.DebuggerDisplayAttribute> は、デバッガー変数ウィンドウでのオブジェクト、プロパティ、フィールドの表示方法を制御します。 この属性は、型、デリゲート、プロパティ、フィールド、アセンブリに適用できます。  
  
 `DebuggerDisplay` 属性の引数は 1 つです。それは、型のインスタンスの値列に表示する文字列です。 この文字列には、中かっこ (`{` と `}`) を含めることができます。 かっこ内のテキストは、フィールド、プロパティ、メソッドとして評価されます。  
  
 クラスにオーバーライドされた `ToString()` メソッドがある場合、デバッガーは、既定の `{<typeName>}` の代わりに、オーバーライドされたメソッドを使用します。 したがって、`ToString()` メソッドをオーバーライドした場合、デバッガーは、既定の `{<typeName>}` の代わりに、オーバーライドされたメソッドを使用し、`DebuggerDisplay` を使用する必要はありません。 両方を使用すると、`DebuggerDisplay` 属性は、オーバーライドされた `ToString()` メソッドよりも優先されます。  
  
 この暗黙的な `ToString()` 呼び出しがデバッガーで評価されるかどうかは、 **[ツール] / [オプション] / [デバッグ]** ダイアログ ボックスのユーザー設定によって異なります。 Visual Basic は、この暗黙的な `ToString()` 評価を実装しません。  
  
> [!IMPORTANT]
>  **[ツール] / [オプション] / [デバッグ]** ダイアログ ボックスで **[オブジェクトの生の構造体を変数ウィンドウに表示する]** チェック ボックスがオンになっている場合、 `DebuggerDisplay` 属性は無視されます。  

> [!NOTE]
> ネイティブ コードは、この属性は C + でのみサポート/cli CLI コード。
  
 次の表に、 `DebuggerDisplay` 属性の使用例と出力例を示します。  
  
|属性|[値] 列に表示される出力|  
|---------------| - |  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> `x` フィールドと `y`フィールドがある型で使用されます。|`x = 5 y = 18`|  
|`[DebuggerDisplay("String value is {getString()}")]`パラメーターの構文は、言語によって異なります。 そのため、使用には注意が必要です。|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` には、名前付きパラメーターも使用できます。  
  
|パラメーター|目的|  
|----------------|-------------|  
|`Name`, `Type`|このパラメーターは、変数ウィンドウの **[名前]** 列と **[型]** 列に影響があります (コンストラクターと同じ構文で、文字列に設定できます)。このパラメーターを乱用したり、不適切に使用したりすると、出力を混乱させる可能性があります。|  
|`Target`, `TargetTypeName`|属性がアセンブリ レベルで使用される場合に、対象の型を指定します。|  
  
 autoexp.cs ファイルは、DebuggerDisplay 属性をアセンブリ レベルで使用します。 autoexp.cs ファイルは、Visual Studio が .NET オブジェクトに対して使用する既定の展開を指定します。 DebuggerDisplay 属性の使用方法について autoexp.cs ファイルで確認したり、autoexp.cs ファイルを変更してコンパイルすることで既定の展開を変更したりできます。 変更する場合は、その前に autoexp.cs ファイルのバックアップを作成してください。  
  
 autoexp.cs をビルドするには、VS2015 の開発者コマンド プロンプトを開いて、次のコマンドを実行します  
  
```cmd
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 autoexp.dll への変更は、次のデバッグ セッションで取得されます。  
  
## <a name="using-expressions-in-debuggerdisplay"></a>DebuggerDisplay での式の使用  
 DebuggerDisplay 属性では、中かっこ内で一般的な式を使用できますが、この方法はお勧めしません。  
  
 DebuggerDisplay で使用される一般的な式は、対象となる型の現在のインスタンスのみの `this` ポインターに暗黙的にアクセスします。 この式には、エイリアス、ローカル、またはポインターに対するアクセスはありません。 式からプロパティを参照しても、そのプロパティに関する属性は処理されません。 たとえば、C# コード `[DebuggerDisplay("Object {count - 2}")]`  では、フィールド `Object 6` が 8 の場合に `count` を表示します。  
  
 DebuggerDisplay で式を使用すると、次のような問題が発生する可能性があります。  
  
- 式の評価はデバッガーで最も負荷のかかる操作であり、式は表示されるたびに評価されます。 これは、コードのステップ実行時にパフォーマンスを低下させる要因になります。 たとえば、コレクションまたは一覧内の値を表示するために使用される複合式は、要素数が多い場合に非常に低速になることがあります。  
  
- 式は、その式が記述された言語の式エバリュエーターではなく、現在のスタック フレームの言語の式エバリュエーターによって評価されます。 これらの言語が異なる場合、予期しない結果が生じる可能性があります。  
  
- 式を評価することにより、アプリケーションの状態が変わる可能性があります。 たとえば、プロパティに値を設定する式は、実行するコード内のプロパティ値を変更します。  
  
  式の評価に関して考えられる問題を回避する方法の 1 つは、操作を実行して文字列を返すプライベート プロパティを作成することです。 これにより、DebuggerDisplay 属性は、そのプライベート プロパティの値を表示できます。 このパターンを実装する例を次に示します。  
  
```csharp  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
public sealed class MyClass   
{      
    public int count { get; set; }      
    public bool flag { get; set; }      
    private string DebuggerDisplay  
   {         
        get  
        {  
             return string.Format("Object {0}", count - 2);  
        }      
    }  
}  
```  
"、Nq"サフィックスが最終的な値を表示するときに、引用符を削除する、式エバリュエーターを示します (nq = 引用符はありません)。 
  
## <a name="example"></a>例  
 次のコード例では、 `DebuggerDisplay`を `DebuggerBrowseable` および `DebuggerTypeProxy`と組み合わせて使用する方法を示します。 **[ウォッチ]** ウィンドウなど、デバッガーの変数ウィンドウに表示されると、次のように展開が作成されます。  
  
|**Name**|**[値]**|**Type**|  
|--------------|---------------|--------------|  
|キー|"three"|object {string}|  
|[値]|3|object {int}|  
  
```csharp  
[DebuggerDisplay("{value}", Name = "{key}")]  
internal class KeyValuePairs  
{  
    private IDictionary dictionary;  
    private object key;  
    private object value;  
    public KeyValuePairs(IDictionary dictionary, object key, object value)  
    {  
        this.value = value;  
        this.key = key;  
        this.dictionary = dictionary;  
    }  
  
    public object Key  
    {  
        get { return key; }  
        set  
        {  
            object tempValue = dictionary[key];  
            dictionary.Remove(key);  
            key = value;  
            dictionary.Add(key, tempValue);  
        }  
    }  
  
    public object Value  
    {  
        get { return this.value; }  
        set  
        {  
            this.value = value;  
            dictionary[key] = this.value;  
        }  
    }  
}  
  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable  
{  
    public Hashtable hashtable;  
  
    public MyHashtable()  
    {  
        hashtable = new Hashtable();    
    }
    
    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
    private class HashtableDebugView  
    {  
        private MyHashtable myhashtable;  
        public HashtableDebugView(MyHashtable myhashtable)  
        {  
            this.myhashtable = myhashtable;  
        }  
  
        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]  
        public KeyValuePairs[] Keys  
        {  
            get  
            {  
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];  
  
                int i = 0;  
                foreach (object key in myhashtable.hashtable.Keys)  
                {  
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);  
                    i++;  
                }  
                return keys;  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>「  
 [DebuggerTypeProxy 属性の使用](../debugger/using-debuggertypeproxy-attribute.md)   
 [マネージド オブジェクトのカスタム ビューの作成](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [C# の書式指定子](../debugger/format-specifiers-in-csharp.md)   
 [デバッガー表示属性によるデバッグ機能の拡張](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
