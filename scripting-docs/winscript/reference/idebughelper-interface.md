---
title: "IDebugHelper インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f0f70ecb8ead264d0d4b074f8fc1d9e3a6091eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelper-interface"></a>IDebugHelper インターフェイス
オブジェクト ブラウザーや単純な接続ポイントに対するファクトリとして機能します。 プロセスのデバッグ マネージャー (PDM) では、スクリプト エンジンによって使用される、このインターフェイスを実装します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugHelper`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|バリアント型をラップするプロパティ ブラウザーを返します。|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|VARIANT をラップして、文字列へのバリアント型の値または VARTYPE 型のカスタム変換できるように、プロパティ ブラウザーを返します。|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|ラップするイベント インターフェイスを返します、指定された`IDispatch`オブジェクト。|