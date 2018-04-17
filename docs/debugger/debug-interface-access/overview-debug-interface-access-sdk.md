---
title: 概要 (Debug Interface Access SDK) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6494ebe261128ba700cbb92467db78a3d77a3600
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="overview-debug-interface-access-sdk"></a>概要 (Debug Interface Access SDK)
DIA SDK を使用して、デバッグ情報を Microsoft にアクセスします。 DIA SDK は、COM ベースの Microsoft デバッグ情報の形式が変更されるたびにコードを再記述する必要がある API セットを提供します。 DIA SDK することもできますを以前のバージョンによって生成される .pdb ファイルと .dbg ファイルで設定されているデバッグ情報の選択のセットから読み取ります[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]5.0 およびそれ以降のバージョン。  
  
 DIA SDK 内の各インターフェイスは、特に記載場所を除く別の COM オブジェクトを表します。 追加のインターフェイスとそのため、追加のオブジェクトが作成、明示的なクエリを使用してなど[idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)または[idiasession::findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)の呼び出しではなく、`QueryInterface`で既存のインターフェイス ポインター。  
  
## <a name="see-also"></a>関連項目  
 [Idiadatasource::opensession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)