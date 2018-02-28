---
title: "IDebugProgramNode2::GetEngineInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 02eaa45746b50da76702e724c700bac166f03017
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
プログラムを実行するデバッグ エンジン (DE) の識別子と名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrEngine`  
 [out]プログラムを実行するデバイスの名前を返します (C++ 固有: これは、呼び出し元が、エンジンの名前に関心がないことを示す null ポインター)。  
  
 `pguidEngine`  
 [out]プログラムを実行する DE のグローバル一意識別子を返します (C++ 固有: これは、呼び出し元が、エンジンの GUID に興味がないことを示す null ポインター)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)