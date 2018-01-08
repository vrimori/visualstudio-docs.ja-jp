---
title: "カスタム パラメーター |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 17a629c2d93bb5e91fb301d4da9dca825e5b8917
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="custom-parameters"></a>カスタム パラメーター
カスタム パラメーターは、ウィザードが開始した後に、ウィザードの操作を制御します。 関連の .vsz ファイルは、統合開発環境 (IDE) でパッケージ化され、ウィザードが開始されたときに、文字列の配列として、ウィザードに渡されるをユーザー定義のパラメーターの配列を提供します。 ウィザードは、文字列の配列を解析し、情報を使用して、ウィザードの実際の操作を制御します。 この方法では、ウィザードが .vsz ファイルの内容によって機能をカスタマイズできます。  
  
 コンテキスト パラメーターは、その一方には、ウィザードが開始されたときに、プロジェクトの状態の機能を定義します。 詳細については、次を参照してください。[コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)です。  
  
 カスタム パラメーターを持つ .vsz ファイルの例を次に示します。  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 .Vsz ファイルの作成者は、パラメーターの値を追加します。 ユーザーが選択すると**新しいプロジェクト**または**新しい項目の追加**でプロジェクトを右クリックし、[ファイル] メニュー**ソリューション エクスプ ローラー**IDE の配列にこれらの値を収集します。文字列。 IDE、プロジェクトの呼び出します<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>フラグのセット、およびプロジェクトの呼び出し、<xref:EnvDTE.IVsExtensibility.RunWizardFile%2A>メソッドには、ウィザードを実行し、結果を返すことを担当します。  
  
 ウィザードは、文字列の配列を解析し、その文字列に対して適切に機能しています。 カスタム パラメーターを実装することによって、この方法でさまざまな機能を実行する 1 つのウィザードを作成できます。 つまり、1 つのウィザードでは、次の 3 つの異なる .vsz ファイルを可能性があります。 各ファイルは、異なる動作を制御するさまざまな状況で、ウィザードのカスタム パラメーターのセットを渡します。  
  
 詳細については、次を参照してください。[ウィザード (です。Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [ウィザード (.Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)