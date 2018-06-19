---
title: 従来の言語サービスにおけるかっこの一致 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9df179d6f5b1bd6d7b9f2c827568b6954860b81
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131964"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>従来の言語サービスにおけるかっこの一致
かっこの照合と、かっこと中かっこなど、同時に、発生する必要がある言語要素の追跡、開発者が役立ちます。 入力すると、開発者、右かっこ、始めかっこが強調表示されます。  
  
 2 つまたは 3 つ同時発生すると呼ばれる要素のペアと 3 要素を照合することができます。 3 要素は、次の 3 つの同時発生する要素のセットです。 たとえば、c# では、`foreach`ステートメントは、3 つの要素をフォーム:"`foreach()`「,」`{`"、および"`}`"です。 右中かっこを入力すると、次の 3 つのすべての要素が強調表示されます。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 中かっこの一致を実装する新しい方法の詳細についてを参照してください。[チュートリアル: 対応する中かっこを表示する](../../extensibility/walkthrough-displaying-matching-braces.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink>クラスは、両方の組み合わせをサポートしているしの 3 倍になり、<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A>と<xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A>メソッドです。  
  
## <a name="implementation"></a>実装  
 言語サービスは、言語でのすべての一致要素を識別し、すべての一致するペアを検索する必要があります。 実装することによってこれは通常<xref:Microsoft.VisualStudio.Package.IScanner>一致する言語とし、使用を検出するために、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>要素と一致するメソッド。  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドは、行をトークン化して、カーソルの直前にトークンを返しますにスキャナーを呼び出します。 スキャナーは、言語要素のペアがのトークンのトリガー値を設定して見つかったことを示します<xref:Microsoft.VisualStudio.Package.TokenTriggers>で現在のトークン。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>をさらに呼び出すメソッドは、<xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A>の解析理由の値を持つメソッド<xref:Microsoft.VisualStudio.Package.ParseReason>を対応する言語要素を検索します。 対応する言語要素が見つかった場合、両方の要素が強調表示されます。  
  
 中かっこを入力することをトリガーする方法、中かっこの強調表示の詳細については、トピックの「解析操作の例」セクションを参照して[レガシ言語サービス パーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)です。  
  
## <a name="enabling-support-for-brace-matching"></a>かっこの照合のサポートを有効にします。  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性を設定できます、 `MatchBraces`、 `MatchBracesAtCaret`、および`ShowMatchingBrace`という名前の対応するプロパティを設定するパラメーター、<xref:Microsoft.VisualStudio.Package.LanguagePreferences>クラスです。 言語の基本設定のプロパティは、ユーザーによっても設定できます。  
  
|レジストリ エントリ|プロパティ|説明|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|有効に中かっこの一致|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|カレットのある有効かっこの一致に移動します。|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|対応するかっこを強調表示されます。|  
  
## <a name="matching-conditional-statements"></a>一致する条件付きステートメント  
 など、条件付きステートメントと照合する`if`、 `else if`、および`else`、または`#if`、 `#elif`、 `#else`、 `#endif`、一致する区切り記号と同じようにします。 サブクラスを作成することができます、<xref:Microsoft.VisualStudio.Package.AuthoringSink>クラスし、一致する要素の内部の配列に区切り記号およびにまたがるテキストを追加できるメソッドを提供します。  
  
## <a name="setting-the-trigger"></a>トリガーの設定  
 次の例では、かっこ、中かっこと角かっこ、および、スキャナーでのトリガーを設定を検出する方法を示します。 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>メソッドを<xref:Microsoft.VisualStudio.Package.Source>クラスは、トリガーを検出し、(このトピックの「一致を検索する」セクションを参照してください)、一致するペアを検索するためにパーサーを呼び出します。 この例では、わかりやすくするためだけです。 スキャナーにメソッドが含まれていると想定`GetNextToken`を識別し、テキストの行からトークンを返します。  
  
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
  
## <a name="matching-the-braces"></a>中かっこに一致します。  
 言語要素 {}、に関するページ ()、および、一致するとするには、その範囲を追加する簡単な例をここでは、<xref:Microsoft.VisualStudio.Package.AuthoringSink>オブジェクト。 この方法は、ソース コードを解析するための推奨アプローチではありません。わかりやすくするためだけになります。  
  
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
 [レガシ言語サービス機能](../../extensibility/internals/legacy-language-service-features1.md)   
 [従来の言語サービスのパーサーとスキャナー](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)