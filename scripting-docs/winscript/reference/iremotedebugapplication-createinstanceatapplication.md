---
title: IRemoteDebugApplication::CreateInstanceAtApplication |Microsoft ドキュメント
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
ms.openlocfilehash: a2185987f6b635dae4d537231fca3327d0aed003
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729072"
---
# <a name="iremotedebugapplicationcreateinstanceatapplication"></a>IRemoteDebugApplication::CreateInstanceAtApplication
コードによって、アプリケーション プロセスでオブジェクトの作成を許可されているのプロセス外アプリケーションにします。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]クラスの id (CLSID) を作成するオブジェクト。  
  
 `pUnkOuter`  
 [in]場合`NULL`集計の一部として、オブジェクトが作成されていません。 それ以外の場合、`pUnkOuter`集約オブジェクトへのポインターは、`IUnknown`インターフェイス (制御`IUnknown`)。  
  
 `dwClsContext`  
 [in]実行可能コードの実行コンテキスト。 値が列挙体から取得されます`CLSCTX`です。  
  
 `riid`  
 [in]オブジェクトとの通信に使用されるインターフェイスの識別子です。  
  
 `ppvObject`  
 [out]要求されたインターフェイス ポインターを受け取るポインター変数のアドレス`riid`です。 成功時に、*`ppvObject`要求されたインターフェイス ポインターを格納します。 障害時に、 \* `ppvObject`含む`NULL`です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドからデリゲートを`CoCreateInstance`です。  
  
## <a name="see-also"></a>関連項目  
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)