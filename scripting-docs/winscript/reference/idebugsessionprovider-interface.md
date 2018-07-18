---
title: IDebugSessionProvider インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e61b1e5e794c68e34250f958cdda0f50b68334c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727142"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider インターフェイス
デバッガーをホストし、言語を有効にする IDE によって提供されるプライマリ インターフェイスは、デバッグを開始します。 実行中のアプリケーションのデバッグ セッションを確立します。 このインターフェイスは、マシンのデバッグ マネージャーによって実装されます。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugSessionProvider`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|指定されたアプリケーションにデバッグ セッションを開始します。|