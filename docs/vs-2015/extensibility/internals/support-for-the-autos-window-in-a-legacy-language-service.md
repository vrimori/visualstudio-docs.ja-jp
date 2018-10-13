---
title: 従来の言語サービスで、[自動変数] ウィンドウのサポート |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 05a3181206f9e73ffe7800a581fc93c3712c4afa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283622"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>従来の言語サービスでの自動変数ウィンドウのサポート
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**[自動変数]** ウィンドウには、変数と (いずれかの理由、ブレークポイントまたは例外)、デバッグ中のプログラムが一時停止すると、スコープ内のパラメーターなどの式が表示されます。 式には、変数、ローカルまたはグローバル、およびローカル スコープで変更されているパラメーターを含めることができます。 **[自動変数]** ウィンドウは、クラス、構造体、またはその他の種類のインスタンスを含めることもできます。 評価できる式エバリュエーターは何も表示できる可能性がある、 **[自動変数]** ウィンドウ。  
  
 Managed package framework (MPF) に直接はサポートされていません、 **[自動変数]** ウィンドウ。 ただし、オーバーライドする場合、<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>メソッドで示される式のリストを返すことができます、 **[自動変数]** ウィンドウ。  
  
## <a name="implementing-support-for-the-autos-window"></a>[自動変数] ウィンドウのサポートを実装します。  
 サポートするために必要な **[自動変数]** ウィンドウを実装するためには、<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。 式のようにソース ファイル内の場所が指定された、実装を決定する必要があります、 **[自動変数]** ウィンドウ。 これでは、各文字列は 1 つの式を表します。 文字列のリストを返します。 戻り値<xref:Microsoft.VisualStudio.VSConstants.S_OK>一覧に、式が含まれていることを示します。 中に<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>を表示する式がないことを示します。  
  
 実際に返される式は、変数やコード内の場所に表示されるパラメーターの名前です。 これらの名前は、値とに表示される、型を取得する式エバリュエーターに渡される、 **[自動変数]** ウィンドウ。  
  
### <a name="example"></a>例  
 次の例の実装を示しています、<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>から式のリストを取得するメソッド、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドを使用する解析理由<xref:Microsoft.VisualStudio.Package.ParseReason>します。 としてラップの各式は、`TestVsEnumBSTR`を実装する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>インターフェイス。  
  
 なお、`GetAutoExpressionsCount`と`GetAutoExpression`メソッドにカスタム メソッドは、`TestAuthoringSink`オブジェクトし、この例をサポートするために追加されました。 追加する式で 1 つの方法を表す、`TestAuthoringSink`パーサーによってオブジェクト (呼び出すことによって、<xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>メソッド) パーサーの外部アクセスできます。  
  
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

