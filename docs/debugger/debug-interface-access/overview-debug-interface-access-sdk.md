---
title: "概要 (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ユーザー定義型"
  - ".dbg ファイル"
  - "モジュール"
  - "インターフェイス [DIA SDK]"
  - "DBG ファイル"
  - "プロシージャ [DIA SDK]"
  - "実行可能ファイル"
  - "COM オブジェクト, DIA SDK"
  - "コンパイル単位"
  - "実行可能イメージ"
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 概要 (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Microsoft のデバッグ情報にアクセスする DIA SDK を使用します。  DIA SDK はMicrosoft がデバッグ情報の形式を変更するたびにコードを記述する必要がなくなった場合COM に基づく API のセットを提供します。  またDIA SDK の割り当てを一連の [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] Version 5.0 以降で生成された .pdb および .dbg ファイルにあるデバッグ情報の以前のバージョンから読み取る。  
  
 DIA SDK の各インターフェイスは他の方法で示される場合別の COM オブジェクトを除き表します。  追加のインターフェイスであるためオブジェクトは明示クエリによって既存のインターフェイス ポインターの `QueryInterface` 呼び出すのではなく[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) または [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) など作成されます。  
  
## 参照  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)