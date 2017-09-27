---
title: "従来の言語サービス内のブレークポイントの検証 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2a87c22948e710a3b95ee7f79b31626794dc7708
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>従来の言語サービス内のブレークポイントを検証します。
ブレークポイントは、デバッガーで実行されている間に特定の時点でプログラムの実行を停止することを示します。 ユーザーは、エディターには、ブレークポイントの有効な場所の構成に関する知識があるないために、ソース ファイル内の任意の行にブレークポイントを配置できます。 デバッガーを起動するときは、実行中のプログラム内の適切な場所にバインドのすべてのマークされたブレークポイント (保留中のブレークポイントと呼ばれます) されます。 ブレークポイントが検証されていることを確認が同時は、有効なコードの場所をマークします。 たとえば、ソース コード内の場所にコードがないため、コメントのブレークポイントが、正しくありません。 デバッガーは、無効なブレークポイントを無効にします。  
  
 言語サービスが表示されているソース コードを知っているために、デバッガーを起動する前に、ブレークポイントを検証できます。 オーバーライドすることができます、<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>ブレークポイントの有効な場所を指定する範囲を返すメソッド。 デバッガーを起動するにデバッガーを読み込むを待機することがなくユーザーに通知が無効なブレークポイントときに、ブレークポイントの場所は検証もします。  
  
## <a name="implementing-support-for-validating-breakpoints"></a>ブレークポイントを検証するためのサポートの実装  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>メソッドには、ブレークポイントの位置が与えられます。 実装には、場所が有効であり、コードを識別するテキスト範囲を返すことによってこれに関連付けられている行の位置ブレークポイントを示すかどうかを決める必要があります。  
  
-   返す<xref:Microsoft.VisualStudio.VSConstants.S_OK>場所が、有効な場合、または<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>が有効でない場合。  
  
-   ブレークポイントが有効な場合は、ブレークポイントと共にテキスト スパンが強調表示されます。  
  
-   ブレークポイントが有効でない場合は、ステータス バーに、エラー メッセージが表示されます。  
  
### <a name="example"></a>例  
 この例の実装を示しています、 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> (存在する場合)、コードの範囲を取得するためにパーサーを指定された場所で呼び出すメソッド。  
  
 この例では、追加されていること、`GetCodeSpan`メソッドを<xref:Microsoft.VisualStudio.Package.AuthoringSink>テキスト範囲を返すことを検証するクラス`true`有効なブレークポイントの位置である場合。  
  
```csharp  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [レガシ言語サービス機能](../../extensibility/internals/legacy-language-service-features1.md)
