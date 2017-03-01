---
title: "従来の言語サービスの [自動変数] ウィンドウのサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 12
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
ms.openlocfilehash: 88cff53ca5c335fdf60aef85d79e9c6e86f03cfa
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>従来の言語サービスの [自動変数] ウィンドウのサポート
**自動変数**  ウィンドウに変数とパラメーター (いずれか、ブレークポイントまたは例外のため)、デバッグ中のプログラムが一時停止されると、スコープ内のような式が表示されます。 式には、変数、ローカルまたはグローバル、およびローカル スコープで変更されているパラメーターを含めることができます。 **自動変数**  ウィンドウでは、クラス、構造体、またはその他の種類のインスタンスを含めることもできます。 評価できる式エバリュエーターは何も表示できる可能性がある、 **[自動変数]**ウィンドウです。  
  
 マネージ パッケージ フレームワーク (MPF) に直接をサポートしていません、 **[自動変数]**ウィンドウです。 ただし、オーバーライドする場合、<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>メソッドを表示する式のリストを返すことができます、 **[自動変数]**ウィンドウ</xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>。  
  
## <a name="implementing-support-for-the-autos-window"></a>[自動変数] ウィンドウのサポートを実装します。  
 サポートするために必要な**[自動変数]**ウィンドウは、<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A><xref:Microsoft.VisualStudio.Package.LanguageService>クラス</xref:Microsoft.VisualStudio.Package.LanguageService>のメソッド</xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>を実装するには 式に表示されるソース ファイル内の場所を指定の実装を決定する必要があります、 **[自動変数]**ウィンドウです。 メソッドでは、各文字列が&1; つの式を表す文字列のリストを返します。 戻り値<xref:Microsoft.VisualStudio.VSConstants.S_OK>一覧に、式が含まれていることを示します中に<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>を表示する式がないことを示します。</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK> 。  
  
 実際に返される式は、変数やコード内の場所に表示されるパラメーターの名前です。 これらの名前は、値とに表示される、型を取得する式エバリュエーターに渡される、 **[自動変数]**ウィンドウです。  
  
### <a name="example"></a>例  
 次の例は、<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A><xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドは、解析理由<xref:Microsoft.VisualStudio.Package.ParseReason>。</xref:Microsoft.VisualStudio.Package.ParseReason>を使用して</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>式のリストを取得するメソッド</xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>の実装を示しています。 としてラップされたそれぞれの式は、`TestVsEnumBSTR`を実装する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>インターフェイス</xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>。  
  
 注意してください、`GetAutoExpressionsCount`と`GetAutoExpression`メソッドにカスタム メソッドは、`TestAuthoringSink`オブジェクトし、この例をサポートするために追加されました。 追加する式で&1; つの方法を表す、`TestAuthoringSink`パーサーによってオブジェクト (を呼び出して、<xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>メソッド)、パーサー外でアクセスできる</xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>。  
  
```c#  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
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
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
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
