---
title: IRemoteDebugApplication::CreateInstanceAtApplication |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CreateInstanceAtApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CreateInstanceAtApplication
ms.assetid: d669ec80-2182-400d-87cc-7c1753315e5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29cbcebc5bdc51be4223b2592bbe6ac3ae76525d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086360"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
コードによって、アプリケーション プロセスでオブジェクトの作成を許可されているのプロセス外アプリケーションにします。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT CreateInstanceAtApplication(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `rclsid`  
 [in]クラスを作成するオブジェクトの識別子 (CLSID)。  
  
 `pUnkOuter`  
 [in]場合`NULL`集計の一部として、オブジェクトが作成されていません。 それ以外の場合、`pUnkOuter`集計オブジェクトへのポインターは、`IUnknown`インターフェイス (制御`IUnknown`)。  
  
 `dwClsContext`  
 [in]実行可能コードを実行するためのコンテキスト。 値が列挙体から取得されます`CLSCTX`します。  
  
 `riid`  
 [in]オブジェクトと通信するために使用するインターフェイスの識別子です。  
  
 `ppvObject`  
 [out]要求されたインターフェイス ポインターを受け取るポインター変数のアドレス`riid`します。 成功時に、*`ppvObject`要求されたインターフェイス ポインターが含まれています。 障害時に、 \* `ppvObject`が含まれています`NULL`します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドからデリゲートを`CoCreateInstance`します。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)