---
title: "SccCloseProject 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCloseProject
helpviewer_keywords: SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d37dc9bff7652856109fb4ec29c8eaa52f1d2507
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="scccloseproject-function"></a>SccCloseProject 関数
この関数は、特定のセッションの終了位置を示す、プロジェクトを閉じます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 ソース管理プラグイン コンテキスト構造体。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|プロジェクトが正常に終了しました。|  
|SCC_E_PROJNOTOPEN|プロジェクトが現在開いていない場合です。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 [SccOpenProject](../extensibility/sccopenproject-function.md)は、この関数の前に必ず呼び出されます。 この関数に対する呼び出しのいずれかを呼び出した後に、`SccOpenProject`関数または[SccUninitialize](../extensibility/sccuninitialize-function.md)、ソース管理システムへの接続を完全に終了します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)