---
title: IDebugSessionProviderEx インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 545b60f13e86e59143ce0e57f454b13f61041f11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726932"
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx インターフェイス
デバッガーのデバッグ ホスト側言語開始を有効に IDE によって提供されるプライマリ インターフェイスです。 実行中のアプリケーションのデバッグ セッションを確立します。 このインターフェイスは、マシン デバッグ マネージャーによって実装されます。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugSessionProviderEx`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|時間内のみのデバッグが、指定したアプリケーションで実行できるかどうかを判断します。|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|指定されたアプリケーションにデバッグ セッションを開始します。|