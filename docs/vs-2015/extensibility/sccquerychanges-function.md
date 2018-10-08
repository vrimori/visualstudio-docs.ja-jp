---
title: SccQueryChanges 関数 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 95f1e5a21ba74779080c601acd42d5deedb75d7c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538660"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[SccQueryChanges 関数](https://docs.microsoft.com/visualstudio/extensibility/sccquerychanges-function)します。  
  
この関数は、指定されたコールバック関数を使用して各ファイルの名前変更に関する情報を提供する、ファイルの一覧を列挙します。  
  
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
 [in]ソース管理プラグインのコンテキストのポインター。  
  
 nFiles  
 [in]ファイルの数`lpFileNames`配列。  
  
 lpFileNames  
 [in]に関する情報を取得するファイル名の配列。  
  
 pfnCallback  
 [in]リスト内の各ファイル名を呼び出すためのコールバック関数 (を参照してください[QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)詳細については)。  
  
 pvCallerData  
 [in]コールバック関数に渡される値は変更されません。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|クエリの処理が正常に完了しました。|  
|SCC_E_PROJNOTOPEN|ソース管理で、プロジェクトが開かれていません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。|  
|SCC_E_NONSPECIFICERROR|指定されていないか、一般的なエラーが発生しました。|  
  
## <a name="remarks"></a>Remarks  
 名前空間に変更を照会する。 具体的には、名前変更、追加、およびファイルを削除します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [エラー コード](../extensibility/error-codes.md)

