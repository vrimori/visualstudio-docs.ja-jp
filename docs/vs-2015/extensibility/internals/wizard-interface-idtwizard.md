---
title: ウィザード インターフェイス (IDTWizard) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb811f0ea6ae3d1be01b5d00f6359503d8f0d581
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538357"
---
# <a name="wizard-interface-idtwizard"></a>ウィザード インターフェイス (IDTWizard)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ウィザード インターフェイス (IDTWizard)](https://docs.microsoft.com/visualstudio/extensibility/internals/wizard-interface-idtwizard)します。  
  
統合開発環境 (IDE) を使用して、<xref:EnvDTE.IDTWizard>ウィザードを使用した通信するインターフェイス。 ウィザードは、IDE でインストールするために、このインターフェイスを実装する必要があります。  
  
 <xref:EnvDTE.IDTWizard.Execute%2A>メソッドは、唯一のメソッドに関連付けられている、<xref:EnvDTE.IDTWizard>インターフェイス。 ウィザードは、このメソッドを実装し、IDE がインターフェイスでメソッドを呼び出します。 次の例では、メソッドのシグネチャを示します。  
  
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
  
 開始機構はどちらも、**新しいプロジェクト**と**新しい項目の追加**ウィザード。 いずれかを開始するを呼び出す、 <xref:EnvDTE.IDTWizard> Dteinternal.h で定義されているインターフェイス。 唯一の違いは、コンテキストとインターフェイスが呼び出されたときに、インターフェイスに渡されるカスタムのパラメーターのセットです。  
  
 次の情報について説明します、<xref:EnvDTE.IDTWizard>インターフェイス ウィザードがで作業するために実装する必要があります、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE。 IDE の呼び出し、<xref:EnvDTE.IDTWizard.Execute%2A>メソッドは、ウィザードで、次を渡します。  
  
-   DTE オブジェクト  
  
     DTE オブジェクトは、オートメーション モデルのルートです。  
  
-   コード セグメントで示すように、ウィンドウの ダイアログ ボックスを識別するハンドル`hwndOwner ([in] long)`します。  
  
     ウィザードを使用してこの`hwndOwner`ウィザード ダイアログ ボックスの親として。  
  
-   コンテキスト パラメーターに渡されるインターフェイス バリアント型の SAFEARRAY、コード セグメントで示すように`[in] SAFEARRAY (VARIANT)* ContextParams`します。  
  
     コンテキスト パラメーターには、開始されているウィザードの種類に固有の値の配列と、プロジェクトの現在の状態が含まれています。 IDE では、ウィザードにコンテキスト パラメーターを渡します。 詳細については、次を参照してください。[コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)します。  
  
-   カスタム パラメーターに渡されるインターフェイス バリアントとしての SAFEARRAY、コード セグメントで示すように`[in] SAFEARRAY (VARIANT)* CustomParams`します。  
  
     カスタム パラメーターには、ユーザー定義のパラメーターの配列が含まれます。 .Vsz ファイルは、IDE にカスタム パラメーターを渡します。 値によって決まりますが、`Param=`ステートメント。 詳細については、次を参照してください。[カスタム パラメーター](../../extensibility/internals/custom-parameters.md)します。  
  
-   インターフェイスの戻り値は、します。  
  
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

