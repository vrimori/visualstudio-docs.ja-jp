---
title: "レガシ API を使用してビューの設定を変更します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] の従来のビュー設定を変更します。"
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# レガシ API を使用してビューの設定を変更します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コア エディターの機能の設定はワード ラップのようなマージン ENT0ENT \[出力\] ダイアログ ボックスでユーザーが仮想空間および変更できます。  ただしこれらの設定をプログラムで変更することもできます。  
  
## 設定のレガシ API を使用して変更します  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> のインターフェイスはテキスト エディターのプロパティを公開します。  テキスト ビューではテキスト ビューのプログラムで変更した設定のグループを表すプロパティ \(\) GUID\_EditPropCategory\_View\_MasterSettings カテゴリが含まれます。  一度ビューの設定は \[ENT4ENT\] ダイアログ ボックスでリセットするまで変更できません。このように変更されました。  
  
 ここではコア エディターのインスタンスのビューの設定を変更するための一般的なプロセスです。  
  
1.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> インターフェイスの `QueryInterface` の呼び出し \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>\)。  
  
2.  `rguidCategory` のパラメーターに GUID\_EditPropCategory\_View\_MasterSettings の値を指定する <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> のメソッドを呼び出します。  
  
     これを行うにはビューの変換プロパティのセットを含む <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> インターフェイスへのポインターを返します。  このグループのどの設定も完全に強制されます。  設定がこのグループには\[ENT2ENT\] ダイアログ ボックスやユーザー コマンドで指定したオプションに従っています。  
  
3.  `idprop` のパラメーターに適切な設定の値を指定する <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> のメソッドを呼び出します。  
  
     たとえばワード ラップ呼び出しの <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> を強制しVSEDITPROPID\_ViewLangOpt\_WordWrap`idprop` の `vt` の値を指定します。  この呼び出しでは`vt` VT\_BOOL は型のバリアントであり`vt.boolVal` は VARIANT\_TRUE です。  
  
## 変更されたレンダリングの設定のリセット  
 コア エディターのインスタンスの変更したビューの構成をリセットするには<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> のメソッドを呼び出して`idprop` のパラメーターに適切な設定値を指定します。  
  
 たとえばワード ラップが自由にフローティング プロパティのカテゴリで <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> を呼び出し`idprop` のパラメーターに VSEDITPROPID\_ViewLangOpt\_WordWrap の値を指定してリスナーを削除します。  
  
 コア エディターの変更されたすべての設定をすぐに削除するにはVSEDITPROPID\_ViewComposite\_AllCodeWindowDefaults の値`idprop` の vt を指定します。  この呼び出しではvt VT\_BOOL は型のバリアントでありvt.boolVal は VARIANT\_TRUE です。  
  
## 参照  
 [コア エディターの内部](../extensibility/inside-the-core-editor.md)   
 [レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [\[オプション\] ダイアログ ボックス](../Topic/Options%20Dialog%20Box%20\(Visual%20Studio\).md)