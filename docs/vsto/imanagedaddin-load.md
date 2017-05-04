---
title: "IManagedAddin::Load | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "IManagedAddin::Load"
  - "Load メソッド"
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# IManagedAddin::Load
  管理対象の VSTO アドインが読み込まれるときに呼び出されます。  
  
## 構文  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### パラメーター  
  
|パラメーター|説明|  
|------------|--------|  
|*bstrManifestURL*|VSTO アドインのマニフェストの完全なパス。|  
|*pdispApplication*|VSTO アドインを読み込むホスト アプリケーションを表す IDispatch のポインター。|  
  
## 戻り値  
 メソッドが正常に完了したかどうかを示す HRESULT 値。  
  
## 解説  
 マニフェストは、VSTO アドインの読み込みに使用される情報を提供するファイル \(通常は XML ファイル\) です。 たとえば、マニフェストには、VSTO アドイン アセンブリの場所や、VSTO アドインが読み込まれるときにインスタンス化するエントリ ポイント クラスを指定できます。  
  
 *bstrManifestURL* パラメーターには、VSTO アドインの HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<アプリケーション名\>*\\Addins\\*\<アドイン ID\>* レジストリ キーの `Manifest` エントリの値が格納されます。 詳細については、「[IManagedAddin インターフェイス](../vsto/imanagedaddin-interface.md)」を参照してください。  
  
 読み込まれる VSTO アドインのアプリケーション ドメインやセキュリティ ポリシーの構成などのタスクを実行するように、[IManagedAddIn::Load](../vsto/imanagedaddin-load.md) メソッドを実装します。  
  
## 参照  
 [IManagedAddin インターフェイス](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  