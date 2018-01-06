---
title: "従来の言語サービスで自動変数 ウィンドウのサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: db6be625c671a508be3c2fd2f1697282af282bdd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>従来の言語サービスで自動変数 ウィンドウのサポート
**自動変数**  ウィンドウに変数とスコープでは、デバッグ中のプログラムには、(いずれかにより、ブレークポイントまたは例外) が一時停止されてパラメーターなどの式が表示されます。 式には、変数、ローカルまたはグローバル、およびローカル スコープで変更されているパラメーターを含めることができます。 **自動変数**  ウィンドウでは、クラス、構造体、またはその他の種類のインスタンスを含めることもできます。 式エバリュエーターが評価できるものに可能性のある表示できる、 **[自動変数]**ウィンドウです。  
  
 Managed package framework (MPF) はの直接サポートを提供していない、 **[自動変数]**ウィンドウです。 ただし、オーバーライドする場合、<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>メソッドで示される式のリストを返すことができます、 **[自動変数]**ウィンドウです。  
  
## <a name="implementing-support-for-the-autos-window"></a>[自動変数] ウィンドウのサポートを実装します。  
 サポートするために必要な**[自動変数]**を実装するのには、ウィンドウ、<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスです。 指定の式のようにソース ファイルの場所に、実装を決定する必要があります、 **[自動変数]**ウィンドウです。 メソッドは、各文字列が 1 つの式を表す文字列の一覧を返します。 戻り値の<xref:Microsoft.VisualStudio.VSConstants.S_OK>一覧に、式が含まれていることを示します、<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>を表示する式がないことを示します。  
  
 実際に返される式は、変数やコード内の場所に表示されるパラメーターの名前です。 これらの名前は、値とで表示される、型を取得する、式エバリュエーターに渡される、 **[自動変数]**ウィンドウです。  
  
### <a name="example"></a>例  
 次の例の実装を示しています、<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>から式のリストを取得するメソッド、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドを使用する解析理由<xref:Microsoft.VisualStudio.Package.ParseReason>です。 それぞれの式としてラップ、`TestVsEnumBSTR`を実装する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>インターフェイスです。  
  
 なお、`GetAutoExpressionsCount`と`GetAutoExpression`メソッドにカスタム メソッドは、`TestAuthoringSink`オブジェクトし、この例をサポートするために追加されました。 追加する式で 1 つの方法を表す、`TestAuthoringSink`パーサーによってオブジェクト (を呼び出して、<xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>メソッド) パーサーの外部アクセスできます。  
  
```csharp  
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