---
title: カスタム パラメーター |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 101076eb863294fe84ffed26d308f67110b90a33
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499453"
---
# <a name="custom-parameters"></a>カスタム パラメーター
カスタム パラメーターは、ウィザードが開始した後に、ウィザードの操作を制御します。 関連 *.vsz*ファイルを統合開発環境 (IDE) でパッケージ化され、ウィザードが開始されると、文字列の配列として、ウィザードに渡されるユーザー定義のパラメーターの配列を提供します。 ウィザードは、文字列の配列を解析し、情報を使用して、ウィザードの実際の操作を制御します。 この方法で、ウィザードがの内容に応じて機能をカスタマイズできます、 *.vsz*ファイル。  
  
 コンテキストのパラメーターは、ウィザードの開始時にその一方で、プロジェクトの状態を定義します。 詳細については、次を参照してください。[コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)します。  
  
 例を次に、 *.vsz*カスタム パラメーターを持つファイル。  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 作成者、 *.vsz*ファイル パラメーターの値を追加します。 ユーザーが選択すると**新しいプロジェクト**または**新しい項目の追加**上、**ファイル**メニューでプロジェクトを右クリックして、または**ソリューション エクスプ ローラー**、IDE文字列の配列には、これらの値を収集します。 IDE を呼び出して、プロジェクトの<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>メソッドを<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>フラグのセット、およびプロジェクトの呼び出し、<xref:EnvDTE.IVsExtensibility.RunWizardFile%2A>ウィザードを実行し、結果を返すことを担当するメソッド。  
  
 ウィザードは、文字列の配列を解析し、文字列に対して適切に機能する責任を負います。 カスタム パラメーターを実装することで、この方法でさまざまな機能を実行する 1 つのウィザードを作成できます。 つまり、1 つのウィザードがあることが 3 つの異なる *.vsz*ファイル。 各ファイルは、異なるさまざまな状況で、ウィザードの動作を制御するカスタムのパラメーターのセットを渡します。  
  
 詳細については、次を参照してください。[ウィザード (.vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [ウィザード (.vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)