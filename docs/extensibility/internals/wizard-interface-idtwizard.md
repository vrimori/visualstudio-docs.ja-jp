---
title: ウィザードのインターフェイス (IDTWizard) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7ebb605ed61cc06ef70fde97f3d5831c6d5c4503
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140704"
---
# <a name="wizard-interface-idtwizard"></a>ウィザードのインターフェイス (IDTWizard)
統合開発環境 (IDE) を使用して、<xref:EnvDTE.IDTWizard>ウィザードと通信するインターフェイスです。 ウィザードは、IDE でインストールするために、このインターフェイスを実装する必要があります。  
  
 <xref:EnvDTE.IDTWizard.Execute%2A>メソッドに関連付けられている唯一の方法では、<xref:EnvDTE.IDTWizard>インターフェイスです。 ウィザードは、このメソッドを実装し、IDE がインターフェイスでメソッドを呼び出します。 次の例は、メソッドのシグネチャを示しています。  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 開始機構は両方と同様、**新しいプロジェクト**と**新しい項目の追加**ウィザード。 開始するにはいずれかを呼び出す、 <xref:EnvDTE.IDTWizard> Dteinternal.h で定義されたインターフェイスです。 唯一の違いは、コンテキストおよびインターフェイスが呼び出されたときに、インターフェイスに渡されるカスタムのパラメーターのセットです。  
  
 次の情報について説明します、<xref:EnvDTE.IDTWizard>インターフェイスで作業するためにウィザードが実装する必要があります、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE です。 IDE の呼び出し、<xref:EnvDTE.IDTWizard.Execute%2A>メソッド ウィザードで、次を渡します。  
  
-   DTE オブジェクト  
  
     DTE オブジェクトは、オートメーション モデルのルートです。  
  
-   コード例で示すように、ウィンドウの ダイアログ ボックスへのハンドル`hwndOwner ([in] long)`です。  
  
     ウィザードを使用してこの`hwndOwner`ウィザード ダイアログ ボックスの親として。  
  
-   コンテキスト パラメーターに渡されるインターフェイス バリアントとして SAFEARRAY のコード例で示すように`[in] SAFEARRAY (VARIANT)* ContextParams`です。  
  
     コンテキスト パラメーターは、ウィザードの開始の種類に固有の値の配列と、プロジェクトの現在の状態を含んでいます。 IDE では、ウィザードにコンテキスト パラメーターを渡します。 詳細については、次を参照してください。[コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)です。  
  
-   カスタム パラメーターに渡されるインターフェイス バリアントとして SAFEARRAY のコード例で示すように`[in] SAFEARRAY (VARIANT)* CustomParams`です。  
  
     カスタム パラメーターには、ユーザー定義のパラメーターの配列が含まれています。 .Vsz ファイルは、IDE にカスタム パラメーターを渡します。 値がによって決定されます、`Param=`ステートメントです。 詳細については、次を参照してください。[カスタム パラメーター](../../extensibility/internals/custom-parameters.md)です。  
  
-   インターフェイスの戻り値には  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>関連項目  
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)   
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [ウィザード (.Vsz) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)