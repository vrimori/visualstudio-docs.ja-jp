---
title: Idiadatasource::opensession |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e4b0e1a1b105f349daed2fea03a290522f3ccb7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547303"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idiadatasource::opensession](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiadatasource-opensession)します。  
  
シンボルを照会するためのセッションを開きます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
|E_INVALIDARG|無効な`ppSession`パラメーター。|  
|E_OUTOFMEMORY|メモリ不足のため、セッションを開きます。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドを開き、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)データ ソースのオブジェクト。  
  
 `IDiaSession` オブジェクトは、データ ソースにクエリを実装します。 セッションでは、デバッグ シンボルのセットごとに 1 つのアドレス空間を管理します。 データ ソースのシンボルによって記述される .exe または .dll ファイルがある場合は、アクティブでは、複数のアドレスの範囲 (たとえば、複数のプロセスでは、読み込まれることがある) ため、し、アドレス範囲ごとに 1 つのセッションを使用する必要があります。  
  
## <a name="example"></a>例  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [概要](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [.Pdb ファイルの照会](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)



