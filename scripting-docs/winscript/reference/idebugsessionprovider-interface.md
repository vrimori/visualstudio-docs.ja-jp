---
title: IDebugSessionProvider インターフェイス |Microsoft Docs
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
ms.openlocfilehash: d6d17546d5461a1ad76b144bf2652672ab4aa675
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345150"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider インターフェイス
デバッガー ホストと言語を有効にする IDE によって提供される主要なインターフェイスでは、デバッグを開始します。 実行中のアプリケーションのデバッグ セッションを確立します。 このインターフェイスは、マシン デバッグ マネージャーによって実装されます。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugSessionProvider`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|指定したアプリケーションのデバッグ セッションを開始します。|