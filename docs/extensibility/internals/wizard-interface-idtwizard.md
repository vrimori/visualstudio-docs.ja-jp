---
title: "ウィザードのインターフェイス (IDTWizard) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDTWizard インターフェイス"
  - "ウィザード、インターフェイス"
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ウィザードのインターフェイス (IDTWizard)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

統合開発環境は \(IDE\)ウィザードとの通信に <xref:EnvDTE.IDTWizard> のインターフェイスを使用します。  ウィザードはこのインターフェイスはIDE でインストールするために実行する必要があります。  
  
 <xref:EnvDTE.IDTWizard.Execute%2A> のメソッドは <xref:EnvDTE.IDTWizard> のインターフェイスに関連付けられているメソッドです。  ウィザードはこのメソッドを実装しインターフェイスのメソッドを呼び出します。  次の例ではメソッドの定義を示しています。  
  
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
  
 起動機能は  **新しいプロジェクト**  と  **新しい項目の追加**  ウィザードの両方に似ています。  またはを起動するには<xref:EnvDTE.IDTWizard> のインターフェイスを Dteinternal.h で定義された呼び出します。  唯一の違いはインターフェイスが呼び出されるとインターフェイスに渡されるカスタム パラメーターおよびコンテキストに設定されます。  
  
 次にウィザードが [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE で動作するように実装する必要がある <xref:EnvDTE.IDTWizard> のインターフェイスについて説明します。  IDE では次の引数を渡しているウィザードの <xref:EnvDTE.IDTWizard.Execute%2A> のメソッドを呼び出しています :  
  
-   DTE オブジェクト  
  
     DTE オブジェクトはオートメーション モデルのルートです。  
  
-   コード セグメント`hwndOwner ([in] long)` に示すようにウィンドウのダイアログ ボックスへのハンドル。  
  
     ウィザードはウィザードのダイアログ ボックスの親コントロールとしてこの `hwndOwner` を使用します。  
  
-   コンテキスト パラメーターはコード セグメントに示すようにSAFEARRAY `[in] SAFEARRAY (VARIANT)* ContextParams` のバリアントとしてインターフェイスに渡されました。  
  
     コンテキスト パラメーターは起動するウィザードの種類に固有のプロジェクトの現在の状態値の配列が含まれます。  IDE ではウィザードにコンテキスト パラメーターを渡します。  詳細については、「[コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)」を参照してください。  
  
-   カスタム パラメーターはコード セグメントに示すようにSAFEARRAY `[in] SAFEARRAY (VARIANT)* CustomParams` のバリアントとしてインターフェイスに渡されました。  
  
     カスタム パラメーターはユーザー定義のパラメーターの配列が含まれます。  .vsz ファイルが IDE にカスタム パラメーターを渡します。  値は `Param=` のステートメントによって決まります。  詳細については、「[カスタム パラメーター](../../extensibility/internals/custom-parameters.md)」を参照してください。  
  
-   インターフェイスの戻り値はです。  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## 参照  
 [コンテキスト パラメーター](../../extensibility/internals/context-parameters.md)   
 [カスタム パラメーター](../../extensibility/internals/custom-parameters.md)   
 [ウィザード](../../extensibility/internals/wizards.md)   
 [ウィザード \(します。Vsz\) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)