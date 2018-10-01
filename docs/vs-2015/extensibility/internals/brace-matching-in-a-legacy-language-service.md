---
title: 従来の言語サービスにおけるかっこの一致 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3a2267805681b092c7a48537e72e5f0ca0b3ecb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534767"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>従来の言語サービスでのかっこの一致
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[従来の言語サービスでかっこの照合](https://docs.microsoft.com/visualstudio/extensibility/internals/brace-matching-in-a-legacy-language-service)します。  
  
かっこの一致には、かっこと中かっこなどに同時発生する必要がある言語要素を追跡する開発者は、役立ちます。 右中かっこを入力すると、開発者は、左中かっこが強調表示されます。  
  
 2 つまたは 3 つに同時発生と呼ばれる要素のペアと 3 要素を照合することができます。 3 要素は、次の 3 つの同時発生要素のセットです。 C# の場合は、たとえばで、`foreach`ステートメントは、3 つの要素をフォーム:"`foreach()`「,」`{`"、および"`}`"。 右中かっこを入力すると、次の 3 つのすべての要素が強調表示されます。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 かっこの一致を実装する新しい方法の詳細についてを参照してください。[チュートリアル: 対応する中かっこを表示する](../../extensibility/walkthrough-displaying-matching-braces.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>クラスは両方のペアをサポートしで 3 倍になり、<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A>と<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A>メソッド。  
  
## <a name="implementation"></a>実装  
 言語サービスは、言語で一致するすべての要素を特定し、すべての一致するペアを検索する必要があります。 実装することによってこれは通常<xref:Microsoft.VisualStudio.Package.IScanner>一致する言語としを使用して検出するために、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>要素と一致するメソッド。  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドは、スキャナー、行をトークン化し、キャレットの直前にトークンが返されます。 スキャナーは、言語要素のペアがのトリガー トークンの値を設定して見つかったことを示します<xref:Microsoft.VisualStudio.Package.TokenTriggers>で現在のトークン。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>メソッドを呼び出して、<xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A>の解析理由の値を持つメソッド<xref:Microsoft.VisualStudio.Package.ParseReason>一致する言語要素を検索します。 一致する言語要素が見つかった場合は、両方の要素が強調表示されます。  
  
 中かっこの強調表示する方法を中かっこを入力するトリガーの詳細については、トピックで「解析操作の例」セクションを参照してください。[レガシ言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)します。  
  
## <a name="enabling-support-for-brace-matching"></a>かっこの一致のサポートを有効にします。  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性が設定できる、 `MatchBraces`、 `MatchBracesAtCaret`、および`ShowMatchingBrace`名前付きパラメーターの対応するプロパティを設定する、<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラス。 言語の基本設定のプロパティは、ユーザーによっても設定できます。  
  
|レジストリ エントリ|プロパティ|説明|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|有効に中かっこの一致|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|カレットのある有効かっこの一致に移動します。|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|対応するかっこを強調表示されます。|  
  
## <a name="matching-conditional-statements"></a>一致する条件付きステートメント  
 条件付きステートメントなどと一致できます`if`、`else if`と`else`、または`#if`、 `#elif`、 `#else`、 `#endif`、一致する区切り記号と同じようにします。 サブクラス化できる、<xref:Microsoft.VisualStudio.Package.AuthoringSink>クラス、および区切り文字に一致する要素の内部配列にまたがるテキストを追加できるメソッドを提供します。  
  
## <a name="setting-the-trigger"></a>トリガーの設定  
 次の例では、かっこ、中かっこと角かっこ、およびスキャナーでは、トリガーの設定を検出する方法を示します。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドを<xref:Microsoft.VisualStudio.Package.Source>クラスは、トリガーを検出し、(このトピックの「一致を検索する」セクションを参照してください)、一致するペアを検索するためにパーサーを呼び出します。 この例では、例示を目的としてのみです。 スキャナーにメソッドが含まれていると想定して`GetNextToken`を識別し、行のテキストからトークンを返します。  
  
```csharp  
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
  
## <a name="matching-the-braces"></a>中かっこの一致  
 言語要素の {}、()、および、一致して追加するには、その範囲の簡略化された例を次に示します、<xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクト。 この方法は、ソース コードの解析に推奨されるアプローチではありません。目的としたものです。  
  
```csharp  
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
  
## <a name="see-also"></a>関連項目  
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [従来の言語サービスのパーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

