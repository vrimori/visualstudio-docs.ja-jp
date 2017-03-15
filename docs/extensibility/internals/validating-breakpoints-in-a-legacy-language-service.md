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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3a8c2df45c0a834430a499cf6a7e7ef2da10bdbf
ms.lasthandoff: 02/22/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>従来の言語サービス内のブレークポイントを検証します。
ブレークポイントは、デバッガーで実行されている間に特定の時点でプログラムの実行を停止することを示します。 ユーザーは、エディターには、ブレークポイントの有効な場所の構成要素の知識があるないために、ソース ファイル内の任意の行にブレークポイントを配置できます。 デバッガーを起動する場合のすべてのマークされているブレークポイント (保留中のブレークポイントと呼ばれます) は実行中のプログラム内の適切な場所にバインドされます。 ブレークポイントが検証されていることを確認が同時に有効なコードの場所をマークします。 たとえば、ソース コードでは、その場所でコードがないため、コメントのブレークポイントが有効でありません。 デバッガーは、無効なブレークポイントを無効にします。  
  
 言語サービスが表示されているソース コードを知っているために、デバッガーが起動される前に、ブレークポイントを検証できます。 オーバーライドすることができます、<xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>ブレークポイントの有効な場所を指定する範囲を返すメソッド</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>。 ブレークポイントの位置は、デバッガーを起動するが、ユーザーには、デバッガーを読み込むを待たずに無効なブレークポイントの通知も検証されます。  
  
## <a name="implementing-support-for-validating-breakpoints"></a>ブレークポイントを検証するためのサポートの実装  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>メソッドには、ブレークポイントの位置が与えられます</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>。 実装には、場所が有効期限、およびコードを識別するテキスト範囲を返すことによってこれに関連付けられている行位置ブレークポイントを指定するかどうかを決める必要があります。  
  
-   返す<xref:Microsoft.VisualStudio.VSConstants.S_OK>場合は、場所が有効、または<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>が有効でない場合</xref:Microsoft.VisualStudio.VSConstants.S_FALSE></xref:Microsoft.VisualStudio.VSConstants.S_OK>。  
  
-   ブレークポイントが有効な場合は、ブレークポイントと共にテキスト範囲が強調表示されます。  
  
-   ブレークポイントが有効でない場合、エラー メッセージがステータス バーに表示されます。  
  
### <a name="example"></a>例  
 この例の実装、 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>(存在する場合)、コードの範囲を取得するためにパーサーを指定された場所で呼び出すメソッド</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>。  
  
 この例では、追加した、`GetCodeSpan`メソッドを<xref:Microsoft.VisualStudio.Package.AuthoringSink>テキスト範囲とを返します検証クラス`true`有効なブレークポイントの位置である場合。</xref:Microsoft.VisualStudio.Package.AuthoringSink> 。  
  
```c#  
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
 [従来の言語サービスの機能](../../extensibility/internals/legacy-language-service-features1.md)
