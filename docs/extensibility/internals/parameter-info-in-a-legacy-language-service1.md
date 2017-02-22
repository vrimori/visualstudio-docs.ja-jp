---
title: "従来の言語サービスでパラメーター情報 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "言語サービス、メソッドのヒント"
  - "メソッドのヒント"
  - "言語サービスでは、パラメーター ヒント]"
  - "IVsMethodData インターフェイス"
  - "パラメーター ヒント (IntelliSense)"
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービスでパラメーター情報
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

IntelliSense パラメーター ヒントでは、言語構成要素にいるについてのヒントを持つユーザーを提供します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 詳細については、次を参照してください。 [エディターと言語サービスの拡張](../../extensibility/extending-the-editor-and-language-services.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
## パラメーター ヒントのツールヒントのしくみ  
 エディターでステートメントを入力すると、VSPackage には、入力中のステートメントの定義を含む小さいツールヒント ウィンドウが表示されます。 たとえば、Microsoft Foundation Classes \(MFC\) ステートメントを入力する場合 \(よう `pMainFrame ->UpdateWindow`\) し、開きかっこは、パラメーターの定義を表示するメソッドのヒントが表示される一覧を作成するキーを押します、 `UpdateWindow` メソッドです。  
  
 パラメーター ヒントのツールヒントは、通常、ステートメント入力候補と組み合わせて使用します。 パラメーターまたはメソッド名またはキーワードの後の書式設定されたその他の情報を持つ言語の最も便利です。  
  
 パラメーター ヒントのツールヒントは、コマンドのインターセプト言語サービスによって開始されます。 ユーザーは、文字を傍受する言語サービス オブジェクトを実装する必要があります、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスし、テキスト ビューへのポインターを渡す、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 実装を呼び出すことによって、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> メソッドで、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> インターフェイスです。 コマンドのフィルターは、コード ウィンドウに入力したコマンドを受け取ります。 ユーザーにパラメーター情報を表示するタイミングを認識するコマンドの情報を監視します。 ステートメント入力候補、エラー マーカーなどの同じコマンド フィルターを使用することができます。  
  
 言語サービスがヒントを提供できるキーワードを入力すると、言語サービスを作成、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> オブジェクトと呼び出し、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> メソッドで、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> にヒントを表示するための IDE を通知するインターフェイスです。 作成、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> オブジェクトを使用して `VSLocalCreateInstance` コクラスを指定して `CLSID_VsMethodTipWindow`です。`VsLocalCreateInstance` 呼び出すヘッダー ファイル vsdoc.h で定義された関数は、 `QueryService` ローカル レジストリおよび呼び出し `CreateInstance` 用には、このオブジェクトで、 `CLSID_VsMethodTipWindow`です。  
  
## メソッドのヒントを提供します。  
 メソッドのヒントを提供するには、呼び出し、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> メソッドに、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> インターフェイスの実装を渡して、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> インターフェイスです。  
  
 ときに、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> クラスが呼び出される、そのメソッドは、次の順序で呼び出されます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     現在のテキスト バッファー内の位置および関連するデータの長さを返します。 これは、ツールヒント ウィンドウでそのデータが隠れないようにするための IDE を指示します。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     最初に表示するメソッドの数 \(0 から始まるインデックス\) を返します。 たとえば、0 を返した場合、最初のオーバー ロードされたメソッドが最初に表示されます。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     現在のコンテキストに適用されるオーバー ロードされたメソッドの数を返します。 値をこのメソッドの 1 より大きい返す場合、テキスト ビューは、するために上矢印および表示されます。 下向きの矢印をクリックすると、IDE を呼び出す、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> メソッドです。 上向きの矢印をクリックすると、IDE を呼び出す、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> メソッドです。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     パラメーター ヒントのツールヒントのテキストは、いくつかの呼び出し時に構築された、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> と <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> メソッドです。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     メソッドに表示するパラメーターの数を返します。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     表示するオーバー ロードに対応するメソッドの数を返す場合は、このメソッドが呼び出された後への呼び出しによって、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> メソッドです。  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     メソッドのヒントが表示されるときに、エディターを更新する、言語サービスに通知します。<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> メソッドを次の呼び出します。  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     呼び出しが表示されたら、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> メソッド ヒントのウィンドウを閉じるときのメソッドです。