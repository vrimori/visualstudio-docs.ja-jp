---
title: IDebugSymbolProviderDirect::GetMethodFromAddress |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8a4f9e99dc1eb0c1cedc6d82690330eb6420098
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880144"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
指定されたデバッグ アドレスには、方法に関する情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAddress`  
 [in]デバッグで表されるアドレス、 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイス。  
  
 `pGuid`  
 [out]モジュールの一意の識別子。  
  
 `pAppID`  
 [out]アプリケーション ドメインの識別子。  
  
 `pTokenClass`  
 [out]外側のクラスを表すトークン。  
  
 `pTokenMethod`  
 [out]モジュールを表すトークン。  
  
 `pdwOffset`  
 [out]先頭からのバイト オフセット、`pAddress`パラメーター。  
  
 `pdwVersion`  
 [out]メソッドのバージョン番号です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)