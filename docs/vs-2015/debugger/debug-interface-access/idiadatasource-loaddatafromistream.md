---
title: Idiadatasource::loaddatafromistream |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14130fbcdc5d7b7dbc4fa60e0026537de79d995d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49929102"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

メモリ内のデータ ストリームを使用してアクセス プログラム データベース (.pdb) ファイルに格納されているデバッグ データを準備します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pIStream  
 [in]<xref:IStream>を使用するデータ ストリームを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 次の表では、このメソッドの戻り値を示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|E_PDB_FORMAT|旧形式のファイルにアクセスしようとしています。|  
|E_INVALIDARG|Invalidparameter します。|  
|E_UNEXPECTED|データ ソースは既に準備されています。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドによってメモリから取得される実行可能ファイルのデバッグ データを使用する、<xref:IStream>オブジェクト。  
  
 検証を伴わない .pdb ファイルを読み込むには、使用、 [idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)メソッド。  
  
 特定の条件に対して、.pdb ファイルを検証するには、使用、 [idiadatasource::loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)メソッド。  
  
 (コールバック機構) を通じてデータの読み込みプロセスにアクセスを使用して、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Idiadatasource::loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)



