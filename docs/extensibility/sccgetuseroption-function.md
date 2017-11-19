---
title: "SccGetUserOption 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetUserOption
helpviewer_keywords: SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebd59cfada6064d40fe48df3cba4eaac3c3293b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption 関数
この関数は、さまざまなユーザー固有のオプションを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 nOption  
 [in](使用できるオプションについては、「解説」を参照してください) を取得するオプションです。  
  
 lpVal  
 [out]オプションに関連付けられている値。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|オプションを正しく取得しました。|  
|SCC_E_OPNOTSUPPORTED|オプションはサポートされていません。|  
|SCC_E_NONSPECIFICERROR|未指定のエラーが発生しました。|  
  
## <a name="remarks"></a>コメント  
 このコマンドでは、次のオプションがサポートされています。  
  
|ユーザー オプション|説明|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|ユーザーがファイルのローカル バージョンをチェック アウトするかどうかを判断します。 `lpVal`割り当てられている`SCC_USEROPT_COLV_YES`(ユーザーがローカル ファイルをチェック アウトする) または`SCC_USEROPT_COLV_NO`です。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [エラー コード](../extensibility/error-codes.md)