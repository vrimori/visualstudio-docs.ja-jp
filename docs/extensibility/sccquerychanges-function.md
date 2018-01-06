---
title: "SccQueryChanges 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccQueryChanges
helpviewer_keywords: SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ec61845433329645fbc4f02a72c062c3cf47f9f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccquerychanges-function"></a>SccQueryChanges 関数
この関数は、指定されたコールバック関数を使用して各ファイルの名前変更に関する情報を提供するファイルのリストを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 nFiles  
 [in]内のファイルの数`lpFileNames`配列。  
  
 lpFileNames  
 [in]に関する情報を取得するファイル名の配列。  
  
 pfnCallback  
 [in]リスト内の各ファイル名に呼び出されるコールバック関数 (を参照してください[QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)詳細)。  
  
 pvCallerData  
 [in]コールバック関数に渡される値が変更されません。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|クエリの処理が正常に完了しました。|  
|SCC_E_PROJNOTOPEN|ソース管理にプロジェクトが開かれていません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。|  
|SCC_E_NONSPECIFICERROR|指定されていないか、一般的なエラーが発生しました。|  
  
## <a name="remarks"></a>コメント  
 照会する変更が、名前空間。 具体的には、名前変更、追加、およびファイルを削除します。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [エラー コード](../extensibility/error-codes.md)