---
title: レガシ言語の Service1 のパラメーター ヒント |Microsoft Docs
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
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 462702fb73cd48f324c02344da5c5ed7c3957f23
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727932"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>従来の言語サービスでのパラメーター ヒント
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

言語構成要素でに関するヒントと IntelliSense のパラメーター ヒントを提供します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は MEF 拡張機能を使用します。 詳細については、次を参照してください。[エディターと言語サービス拡張](../../extensibility/extending-the-editor-and-language-services.md)します。  
  
> [!NOTE]
>  新しいエディターの API をできるだけ早く使用を開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用することができます。  
  
## <a name="how-parameter-info-tooltips-work"></a>パラメーター ヒントのツールヒントのしくみ  
 エディターでステートメントを入力すると、VSPackage に型指定されているステートメントの定義を含む小さいツールヒント ウィンドウが表示されます。 たとえば、Microsoft Foundation Classes (MFC) ステートメントを入力する場合 (など`pMainFrame ->UpdateWindow`) とかっこが、パラメーターの定義を表示するメソッドのヒントが表示される一覧を作成するキーを押して、`UpdateWindow`メソッド。  
  
 パラメーター ヒントのツールヒントは、通常、ステートメント入力候補と組み合わせて使用します。 パラメーターまたはメソッドの名前やキーワードの後に書式設定されたその他の情報を持つ言語に最も適しています。  
  
 パラメーター ヒントのツールヒントは、コマンド インターセプション経由で、言語サービスによって開始されます。 ユーザーの文字をインターセプトする、言語サービス オブジェクトを実装する必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスし、テキスト ビューへのポインターを渡す、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>実装を呼び出すことによって、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>インターフェイス。 コマンドのフィルターは、コード ウィンドウに入力したコマンドを受け取ります。 ユーザーにパラメーター情報を表示するタイミングを知るコマンド情報を監視します。 ステートメント入力候補やエラーのマーカーなどの同じコマンド フィルターを使用することができます。  
  
 言語サービスがヒントを提供できるキーワードを入力すると、言語サービスを作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>オブジェクトと呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>ヒントを表示するための IDE に通知するインターフェイス。 作成、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>オブジェクトを使用して`VSLocalCreateInstance`コクラスを指定して`CLSID_VsMethodTipWindow`します。 `VsLocalCreateInstance` 呼び出すヘッダー ファイル vsdoc.h で定義された関数は、`QueryService`ローカル レジストリおよび呼び出し`CreateInstance`用には、このオブジェクトで、`CLSID_VsMethodTipWindow`します。  
  
## <a name="providing-a-method-tip"></a>メソッドのヒントを提供します。  
 呼び出すメソッドのヒントを提供する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>メソッドで、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>インターフェイスの実装に渡す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>インターフェイス。  
  
 ときに、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>クラスが呼び出される、そのメソッドは、次の順序で呼び出されます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     現在のテキスト バッファーの位置と、関連するデータの長さを返します。 これには、IDE でツールヒント ウィンドウでそのデータが見えにくくならないように指示します。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     最初に表示するメソッドの数 (0 から始まるインデックス) を返します。 たとえば、0 を返した場合、最初のオーバー ロードされたメソッドが最初に表示されます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     現在のコンテキストで適用されるオーバー ロードされたメソッドの数を返します。 値をこのメソッドの 1 より大きい返すし、テキスト ビューに上矢印と表示されます。 下矢印をクリックすると、IDE を呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A>メソッド。 上向きの矢印をクリックすると、IDE を呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A>メソッド。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     パラメーター ヒントのツールヒントのテキストは、いくつかの呼び出し時に構築された、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>と<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>メソッド。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     メソッドで表示するパラメーターの数を返します。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     表示するオーバー ロードに対応するメソッドの数を返す場合、このメソッドは呼び出されるへの呼び出し後に、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>メソッド。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     メソッドのヒントが表示されたら、エディターを更新する、言語サービスに通知します。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>メソッドでは、次の呼び出し。  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     呼び出しを受信する、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>メソッド メソッド ヒントのウィンドウを閉じるとき。

