---
title: IScriptEntry インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d7b33e2e5c90d5c489fe283575b4a2e45671f9a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349349"
---
# <a name="iscriptentry-interface"></a>IScriptEntry インターフェイス
実装するオブジェクト、`IScriptEntry`インターフェイスはスクリプト ブロックまたは関数オブジェクトのいずれかを表します。  
  
 継承されたメソッドだけでなく`IScriptNode`、`IScriptEntry`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|本文に対応するテキストを返します、`IScriptEntry`スクリプト ブロック、関数のブロックまたはスクリプトレットします。|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|識別する項目の名前を返します、`IScriptEntry`オブジェクト。|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|(関数) などの 1 つのオブジェクトを表すエントリの場合は、オブジェクトの名前を返します。|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|開始位置とエントリの長さを返します。|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|型の情報を返します、`IScriptEntry`関数オブジェクト。|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|対応するテキストを返します、`IScriptEntry`スクリプト ブロック、またはソース コードに含まれている、`IScriptScriptlet`イベント ハンドラー。|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|本文内にあるテキストを設定、`IScriptEntry`スクリプト ブロックまたは`IScriptScriptlet`スクリプトレットします。|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|識別する項目の名前を設定、`IScriptEntry`オブジェクト。|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|(関数) などの 1 つのオブジェクトを表すエントリの場合は、オブジェクトの名前を設定します。|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|セットの情報を入力する、`IScriptEntry`関数オブジェクト。|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|対応するテキストを設定、`IScriptEntry`スクリプト ブロック、またはソース コードに含まれている、`IScriptScriptlet`イベント ハンドラー。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)