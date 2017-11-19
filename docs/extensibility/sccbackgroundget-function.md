---
title: "SccBackgroundGet 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccBackgroundGet
helpviewer_keywords: SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85b700f0cb1e3a364cae69ff6c628151ea6a7bd3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 関数
この関数は、ソース管理から各指定されたファイルのユーザー操作なしで取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccBackgroundGet(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LONG    dwFlags,  
   LONG    dwBackgroundOperationID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [入力、出力].取得するファイルの名前の配列。  
  
> [!NOTE]
>  名前は、完全修飾のローカル ファイル名である必要があります。  
  
 dwFlags  
 [in]コマンドのフラグ (`SCC_GET_ALL`、 `SCC_GET_RECURSIVE`)。  
  
 dwBackgroundOperationID  
 [in]この操作に関連付けられている一意の値。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|操作が正常に完了しました。|  
|SCC_E_BACKGROUNDGETINPROGRESS|バック グラウンドの取得が既に進行中 (ソース管理プラグインを返すこの同時バッチ操作はサポートされていない場合にのみ)。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
  
## <a name="remarks"></a>コメント  
 この関数は常にソース管理プラグインが読み込まれている 1 つから別のスレッドで呼び出されます。 この関数が完了するまでを返す必要はありません。ただし、その複数回と共に呼び出せる複数同時にすべてのファイルのリスト。  
  
 使用、`dwFlags`と同じ引数が、 [SccGet](../extensibility/sccget-function.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGet](../extensibility/sccget-function.md)