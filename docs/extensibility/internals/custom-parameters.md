---
title: "カスタム パラメーター | Microsoft Docs"
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
  - "ウィザードでは、カスタム パラメーター"
  - "カスタム パラメーター"
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# カスタム パラメーター
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

カスタム パラメーターはウィザードが起動したらウィザードの操作を制御します。  関連 .vsz ファイルはウィザードの起動時に統合開発環境でパッケージ化され\(IDE\) ウィザードに文字列の配列として渡されるユーザー定義のパラメーターが用意されています。  ウィザードは文字列の配列を解析しウィザードの実際の処理を制御するために情報を使用します。  こうすると.vsz ファイルで機能をカスタマイズできます。  
  
 コンテキスト パラメーターはウィザードの起動時にプロジェクトのステータスを定義します。  詳細については、「[コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)」を参照してください。  
  
 ここではカスタム パラメーターを持つ .vsz ファイルの例です :  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .vsz ファイルの作成者はパラメーターの値を追加します。  ユーザーが \[ファイル\] メニューのまたは  **ソリューション エクスプローラー**  でプロジェクトを右クリックして **新しい項目の追加**  \[入力\] ENT0ENT を選択するとIDE では文字列の配列に値を収集します。  IDE では<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> フラグを設定してプロジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> のメソッドを呼び出してウィザードを実行し結果を返す原因となった <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> のメソッドを呼び出します。  
  
 ウィザードは文字列の配列を適切に解析と文字列の機能があります。  これによりカスタム パラメーターを実行してさまざまな機能を実行する 1 人のウィザードを作成できます。  つまり1 人のウィザードは3 種類の .vsz ファイルがあるとします。  各ファイルはさまざまな場合はウィザードの動作を制御するカスタム パラメーターのセットを渡します。  
  
 詳細については、「[ウィザード \(します。Vsz\) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [ウィザード \(します。Vsz\) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)