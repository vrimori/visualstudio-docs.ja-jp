---
title: "Idiadatasource::opensession |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6b7cfaf3e2cf7331576ca79b9820bafb761fc44c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 次の表は、このメソッドの戻り値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)シンボルのソースにオブジェクトが既に初期化されていません。|  
|E_INVALIDARG|無効な`ppSession`パラメーター。|  
|E_OUTOFMEMORY|メモリ不足のため、セッションを開きます。|  
  
## <a name="remarks"></a>コメント  
 このメソッドを開き、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)データ ソース用オブジェクトです。  
  
 `IDiaSession`オブジェクトは、データ ソースにクエリを実装します。 セッションでは、デバッグ シンボルのセットごとに 1 つのアドレス空間を管理します。 データ ソースのシンボルによって記述される .exe または .dll ファイルが場合は、複数のアドレスでアクティブな範囲は (たとえば、複数のプロセスでは、読み込まれることがある) ため、その各アドレス範囲の 1 つのセッションを使用する必要があります。  
  
## <a name="example"></a>例  
  
```C++  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>参照  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)