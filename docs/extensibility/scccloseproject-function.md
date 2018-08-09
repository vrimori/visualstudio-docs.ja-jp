---
title: SccCloseProject 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 49d3196fbe2eb6c3bafa1ec234e27072e50a4b7d
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636026"
---
# <a name="scccloseproject-function"></a>SccCloseProject 関数
この関数は、特定のセッションの終了位置を示す、プロジェクトを閉じます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
### <a name="parameters"></a>パラメーター  
 pvContext  
 ソース管理プラグイン コンテキスト構造体。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|プロジェクトが正常に閉じられました。|  
|SCC_E_PROJNOTOPEN|プロジェクトは、現在開いているではありません。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 [SccOpenProject](../extensibility/sccopenproject-function.md)は常にこの関数の前に呼び出されます。 この関数の呼び出しのいずれかへの呼び出し後は、`SccOpenProject`関数または[SccUninitialize](../extensibility/sccuninitialize-function.md)、ソース管理システムへの接続を完全に終了します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)