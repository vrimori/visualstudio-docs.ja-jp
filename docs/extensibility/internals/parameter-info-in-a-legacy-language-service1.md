---
title: レガシ言語 Service1 のパラメーター ヒント |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50450d1968c626e0a5b32dee4c6f03d005d6ede9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-info-in-a-legacy-language-service"></a>従来の言語サービスでのパラメーター ヒント
IntelliSense パラメーター ヒントでは、言語コンストラクトにいる場所に関するヒントを使用してユーザーを提供します。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 詳細については、次を参照してください。[エディターと言語サービスの拡張](../../extensibility/extending-the-editor-and-language-services.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## <a name="how-parameter-info-tooltips-work"></a>パラメーター ヒントのツールヒントが機能するしくみ  
 エディターでステートメントを入力すると、VSPackage に型指定されているステートメントの定義を含む小さいツールヒント ウィンドウが表示されます。 たとえば、Microsoft Foundation Classes (MFC) ステートメントを入力する場合 (など`pMainFrame ->UpdateWindow`) と始めかっこが、パラメーターの定義を表示するメソッドのヒントが表示される一覧を作成するキーを押して、`UpdateWindow`メソッドです。  
  
 パラメーター ヒントのツールヒントは通常、ステートメント入力候補と組み合わせて使用されます。 これらは、パラメーターまたはメソッド名またはキーワードの後に書式設定された他の情報を持つ言語の最も役立ちます。  
  
 パラメーター ヒントのツールヒントは、コマンド インターセプト言語サービスによって開始されます。 ユーザーの文字を傍受する言語サービス オブジェクトを実装する必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスし、テキスト ビューへのポインターを渡す、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>実装では、呼び出すことによって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>インターフェイスです。 コマンドのフィルターは、コード ウィンドウに入力したコマンドを受け取ります。 ユーザーにパラメーター情報を表示するタイミングを調べるコマンド情報を監視します。 ステートメント入力候補、エラー マーカーなどの同じコマンド フィルターを使用することができます。  
  
 言語サービスがヒントを提供できるキーワードを入力すると、言語サービスを作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>オブジェクトと呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>ヒントを表示するための IDE に通知するインターフェイスです。 作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>オブジェクトを使用して`VSLocalCreateInstance`コクラスを指定して`CLSID_VsMethodTipWindow`です。 `VsLocalCreateInstance` 呼び出すヘッダー ファイル vsdoc.h で定義された関数は、`QueryService`ローカル レジストリおよび呼び出し`CreateInstance`このオブジェクトに対して、`CLSID_VsMethodTipWindow`です。  
  
## <a name="providing-a-method-tip"></a>メソッドのヒントを提供します。  
 メソッドのヒントを提供するには、呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>インターフェイスの実装を渡して、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>インターフェイスです。  
  
 ときに、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>クラスが呼び出される、そのメソッドは、次の順序で呼び出されます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     現在のテキスト バッファー内の位置および関連するデータの長さを返します。 これは、ツールヒント ウィンドウでそのデータが隠れないようにするための IDE を指示します。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     最初に表示するメソッドの数 (0 から始まるインデックス) を返します。 たとえば、0 を返した場合、最初のオーバー ロードされたメソッドが最初に表示されます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     現在のコンテキストに適用できるオーバー ロードされたメソッドの数を返します。 値を返す場合このメソッドの 1 より大きい、し、テキスト ビューは、するのに上矢印および下矢表示されます。 IDE を呼び出す場合は、下矢印をクリックして、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A>メソッドです。 上向きの矢印をクリックすると、IDE を呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A>メソッドです。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     パラメーター ヒントのツールヒントのテキストがいくつかの呼び出し時に構築された、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>メソッドです。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     メソッドに表示するパラメーターの数を返します。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     表示する、オーバー ロードに対応するメソッドの数を返す場合このメソッドが呼び出された後への呼び出しによって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>メソッドです。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     メソッドのヒントが表示されるときに、エディターを更新するように言語サービスに通知します。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>メソッド、次を呼び出します。  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     呼び出しが表示されたら、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>メソッド メソッド ヒント ウィンドウを閉じるとき。