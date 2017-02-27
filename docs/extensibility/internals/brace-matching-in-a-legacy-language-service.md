---
title: "従来の言語サービスにおけるかっこの一致 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自動一致"
  - "言語サービス [マネージ パッケージ フレームワーク] かっこの一致"
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# 従来の言語サービスにおけるかっこの一致
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

かっこの一致には、かっこと中かっこなど同時に発生する必要がある言語要素の追跡、開発者ことができます。 右中かっこを入力すると、開発者は、左中かっこが強調表示されます。  
  
 2 つまたは 3 つ同時発生すると呼ばれる要素のペアと組を照合することができます。 3 要素は、次の 3 つの同時発生する要素のセットです。 などで、C\# の場合、 `foreach` ステートメントは、3 つの要素をフォーム:"`foreach()`「,」`{`"、および"`}`"です。 右中かっこを入力すると、すべての 3 つの要素が強調表示されます。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 中かっこの一致を実装する新しい方法の詳細を参照してください [チュートリアル: 対応する中かっこの表示](../../extensibility/walkthrough-displaying-matching-braces.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> クラスは、2 つのペアをサポートしているしで 3 倍になり、 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> と <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> メソッドです。  
  
## 実装  
 言語サービスは、言語ですべての一致要素を識別し、すべての一致するペアを検索する必要があります。 実装することによってこれは通常 <xref:Microsoft.VisualStudio.Package.IScanner> かを検出、一致する言語を使用して、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 要素に一致するメソッドです。  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> メソッドは、スキャナー、行のトークンを作成し、キャレットの直前にトークンが返されます。 スキャナーは、言語要素のペアがのトークンのトリガー値を設定して見つかったことを示す <xref:Microsoft.VisualStudio.Package.TokenTriggers> 現在のトークンにします。<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> メソッドの呼び出し、 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> を順番に呼び出すメソッドは、 <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> の解析のための値を持つメソッド <xref:Microsoft.VisualStudio.Package.ParseReason> 一致する言語要素を検索します。 一致する言語要素が検出されると、両方の要素が強調表示されます。  
  
 中かっこの入力をトリガーする方法、中かっこの強調表示の詳細については、トピックで「解析操作の例」を参照してください [従来の言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)します。  
  
## かっこの一致のサポートを有効にします。  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 属性を設定できる、 `MatchBraces`, 、`MatchBracesAtCaret`, と `ShowMatchingBrace` 名前付きパラメーターの対応するプロパティを設定する、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> クラスです。 言語の基本設定のプロパティは、ユーザーによっても設定できます。  
  
|レジストリ エントリ|プロパティ|説明|  
|----------------|-----------|--------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|有効に中かっこの一致|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|キャレットとして有効にかっこの一致に移動します。|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|対応する中かっこを強調表示されます。|  
  
## 一致する条件付きステートメント  
 条件付きステートメントをなどと一致できます `if`, 、`else if`, 、および `else`, 、または `#if`, 、`#elif`, 、`#else`, 、`#endif`, 、一致する区切り記号と同じようにします。 サブクラス化することができます、 <xref:Microsoft.VisualStudio.Package.AuthoringSink> クラスし、区切り文字に一致する要素の内部配列だけでなくにまたがるテキストを追加するメソッドを提供します。  
  
## トリガーの設定  
 次の例では、対応するかっこ、中かっこと角かっこおよびスキャナーにして、トリガーの設定を検出する方法を示します。<xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> メソッドを <xref:Microsoft.VisualStudio.Package.Source> クラスは、トリガーを検出し、\(このトピックの「一致を検索する」を参照してください\) 一致するペアが検出するためパーサーを呼び出します。 この例では、説明の目的でのみです。 スキャナーにメソッドが含まれていると想定して `GetNextToken` を識別し、テキストの行からトークンを返します。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private const string braces = "()[]{}";  
        private Lexer lex;  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar) && token.Length > 0)  
                {  
                    if (braces.IndexOf(firstChar) != -1)  
                    {  
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;  
                    }  
                }  
            }  
            return foundToken;  
        }  
```  
  
## 中かっこに一致します。  
 言語要素の {}、\(\)、およびで一致して、それらの範囲を追加するための簡単な例をここでは、 <xref:Microsoft.VisualStudio.Package.AuthoringSink> オブジェクトです。 この方法はソース コードを解析する方法をお勧めはできません。説明のためになります。  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class Parser  
    {  
         private IList<TextSpan[]> m_braces;  
         public IList<TextSpan[]> Braces  
         {  
             get { return m_braces; }  
         }  
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             if IsMatch(braceSpan1, braceSpan2)  
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });  
         }  
  
         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)  
         {  
             //definition for matching here  
          }  
    }  
  
    public class TestLanguageService : LanguageService  
    {  
         Parser parser = new Parser();  
         Source source = (Source) this.GetSource(req.FileName);  
  
         private AuthoringScope ParseSource(ParseRequest req)  
         {  
             if (req.Sink.BraceMatching)  
             {  
                 if (req.Reason==ParseReason.MatchBraces)  
                 {  
                     foreach (TextSpan[] brace in parser.Braces)  
                     {  
                         req.Sink.MatchPair(brace[0], brace[1], 1);  
                     }  
                 }  
             }  
             return new TestAuthoringScope();  
         }  
    }  
}  
```  
  
## 参照  
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [従来の言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)