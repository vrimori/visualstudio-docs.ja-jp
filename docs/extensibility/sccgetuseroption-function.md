---
title: "SccGetUserOption 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetUserOption"
helpviewer_keywords: 
  - "SccGetUserOption 関数"
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGetUserOption 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、さまざまなユーザー固有のオプションを取得します。  
  
## 構文  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### パラメーター  
 pContext  
 \[in\]ソース管理プラグインのコンテキストのポインター。  
  
 nOption  
 \[in\]\(使用できるオプションについては、「解説」を参照してください\) を取得するオプションです。  
  
 lpVal  
 \[out\]オプションに関連付けられている値です。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|オプションは、正常に取得しました。|  
|SCC\_E\_OPNOTSUPPORTED|オプションがサポートされていません。|  
|SCC\_E\_NONSPECIFICERROR|不明なエラーが発生しました。|  
  
## 解説  
 このコマンドでは、次のオプションがサポートされています。  
  
|ユーザー オプション|説明|  
|----------------|--------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|ユーザーがファイルのローカル バージョンをチェック アウトするかどうかを決定します。`lpVal` 割り当てられている `SCC_USEROPT_COLV_YES` \(ユーザーがローカル ファイルをチェック アウトする\) または `SCC_USEROPT_COLV_NO`です。|  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [エラー コード](../extensibility/error-codes.md)