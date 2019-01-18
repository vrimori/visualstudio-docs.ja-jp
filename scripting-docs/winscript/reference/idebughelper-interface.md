---
title: IDebugHelper インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba760dc15cc0a3d3f2f0d80f3a16c5621582bc11
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347477"
---
# <a name="idebughelper-interface"></a>IDebugHelper インターフェイス
オブジェクト ブラウザーと単純な接続ポイントのためのファクトリとして機能します。 プロセス デバッグ マネージャー (PDM) は、スクリプト エンジンによって使用される、このインターフェイスを実装します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugHelper`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|バリアント型をラップするプロパティ ブラウザーを返します。|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|バリアントをラップし、VARIANT 値または VARTYPE 型の文字列にカスタムの変換では、プロパティ ブラウザーを返します。|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|ラップするイベント インターフェイスを返します、指定された`IDispatch`オブジェクト。|