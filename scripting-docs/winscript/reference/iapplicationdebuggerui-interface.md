---
title: "IApplicationDebuggerUI インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IApplicationDebuggerUI interface
ms.assetid: b8828817-ca24-4012-802c-7dcaeea65dc8
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbaa04f6790ffc4d80447a6745ca82cc8dba6802
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iapplicationdebuggerui-interface"></a>IApplicationDebuggerUI インターフェイス
デバッガー統合開発環境 (IDE) によって実装される (他に、 `IApplicationDebugger`)、外部コンポーネントにデバッガーのユーザー インターフェイス (UI) より詳細に制御を提供します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IApplicationDebuggerUI`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IApplicationDebuggerUI::BringDocumentToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumenttotop.md)|デバッガーでは、最上位に指定されたデバッグ ドキュメントを含むウィンドウのユーザー インターフェイスを表示します。|  
|[IApplicationDebuggerUI::BringDocumentContextToTop](../../winscript/reference/iapplicationdebuggerui-bringdocumentcontexttotop.md)|デバッガーのユーザー インターフェイスでは、最上位に指定されたドキュメントのコンテキストを含むウィンドウを表示し、コンテキストにウィンドウをスクロールします。|