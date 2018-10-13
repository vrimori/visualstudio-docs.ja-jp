---
title: IDebugSymbolProviderDirect::GetCurrentModulesState |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e267cfdead3b78199f4a71bf1ada3ae8cce27e99
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256088"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

シンボル プロバイダーがメンバーであるシンボルのグループに関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetCurrentModulesState(  
    DWORD*          pState,  
    unsigned long * count  
);  
```  
  
```csharp  
int GetCurrentModulesState(  
    out uint pState,  
    out uint count  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pState`  
 [out]シンボル プロバイダー グループの状態。  
  
 `count`  
 [out]グループ内のモジュールの数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 モジュールの追加、またはシンボルのグループから削除されるたびに、状態が変更されます。 そのため、このメソッドは、シンボルのグループが変更されたかどうかを検出するために使用できます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)

