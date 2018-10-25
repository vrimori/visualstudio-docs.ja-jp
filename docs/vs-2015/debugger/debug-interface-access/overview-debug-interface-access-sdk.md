---
title: 概要 (Debug Interface Access SDK) |Microsoft Docs
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
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 741e4ee8e7b05db9d8b63b296569e268d7144dc7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193610"
---
# <a name="overview-debug-interface-access-sdk"></a>概要 (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

DIA SDK を使用して、Microsoft のデバッグ情報にアクセスします。 DIA SDK では、COM ベースの Microsoft デバッグ情報の形式が変更されるたびにコードを書き直す必要がなくなります API セットを提供します。 DIA SDK では以前のバージョンによって生成される .pdb ファイルと .dbg ファイルで設定されているデバッグ情報の一部から読み取ることもできます[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]5.0 以降のバージョン。  
  
 DIA SDK 内の各インターフェイスは、それ以外の場合に記載されている場合を除く別の COM オブジェクトを表します。 追加のインターフェイス、およびその他のオブジェクトが作成、明示的なクエリを使用してなど[idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)または[idiasession::findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)を呼び出すことではなく、`QueryInterface`で既存のインターフェイス ポインター。  
  
## <a name="see-also"></a>関連項目  
 [Idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)



