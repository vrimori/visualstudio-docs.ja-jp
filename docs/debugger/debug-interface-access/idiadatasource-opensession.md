---
title: Idiadatasource::opensession |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bea16f7ff0f723979ded9962a8ff9e620227f8ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843113"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
シンボルを照会するためのセッションを開きます。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 ppSession  
 [out]返します、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)開いているセッションを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 次の表では、このメソッドの戻り値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)シンボルのソースとオブジェクトが既に初期化されていません。|  
|E_INVALIDARG|無効な `ppSession` パラメーター。|  
|E_OUTOFMEMORY|メモリ不足のため、セッションを開きます。|  
  
## <a name="remarks"></a>コメント  
 このメソッドを開き、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)データ ソースのオブジェクト。  
  
 `IDiaSession` オブジェクトは、データ ソースにクエリを実装します。 セッションでは、デバッグ シンボルのセットごとに 1 つのアドレス空間を管理します。 データ ソースのシンボルによって記述される .exe または .dll ファイルがある場合は、アクティブでは、複数のアドレスの範囲 (たとえば、複数のプロセスでは、読み込まれることがある) ため、し、アドレス範囲ごとに 1 つのセッションを使用する必要があります。  
  
## <a name="example"></a>例  
  
```C++  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>「  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)