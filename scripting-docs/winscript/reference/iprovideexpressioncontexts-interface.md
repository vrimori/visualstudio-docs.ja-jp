---
title: IProvideExpressionContexts インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91f4251fec57001ba6c7a4ea1804ec72371418bb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345098"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts インターフェイス
特定のコンポーネントによって認識されている式コンテキストを列挙する手段を提供します。 スクリプト エンジンは、通常、このインターフェイスを実装します。  
  
 プロセス デバッグ マネージャーでは、このインターフェイスを使用して、特定のスレッドに関連付けられているすべてのグローバル式のコンテキストを見つけます。  
  
> [!NOTE]
>  このインターフェイスは、関心のあるスレッド内からを呼び出されます。 現在のスレッドを識別して適切な列挙子を返すために、実装者の責任です。  
  
## <a name="methods"></a>メソッド  
 継承されたメソッドだけでなく`IUnknown`、`IProvideExpressionContexts`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|このコンポーネントによって認識されている式コンテキストの列挙子を返します。|