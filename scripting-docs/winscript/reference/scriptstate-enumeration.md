---
title: SCRIPTSTATE 列挙型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTSTATE enum
ms.assetid: 5f5deb05-c4bb-4964-8077-e624c6b2a14e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35e062a9c2f3076144063ffb77895c8a03ecc4ac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734282"
---
# <a name="scriptstate-enumeration"></a>SCRIPTSTATE 列挙型
スクリプト エンジンの状態を指定します。 この列挙は使用、 [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) 、 [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) 、および[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum tagSCRIPTSTATE {  
    SCRIPTSTATE_UNINITIALIZED = 0,  
    SCRIPTSTATE_INITIALIZED   = 5,  
    SCRIPTSTATE_STARTED       = 1,  
    SCRIPTSTATE_CONNECTED     = 2,  
    SCRIPTSTATE_DISCONNECTED  = 3,  
    SCRIPTSTATE_CLOSED        = 4  
} SCRIPTSTATE;  
```  
  
## <a name="enumeration-values"></a>列挙値  
  
|||  
|-|-|  
|SCRIPTSTATE_UNINITIALIZED|スクリプトは作成したばかりがまだ初期化されていないを使用して、`IPersist*`インターフェイスと[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)です。|  
|SCRIPTSTATE_INITIALIZED|スクリプトが初期化されてがありません (その他のオブジェクトへの接続またはイベントをシンク) を実行しているか、コードを実行します。 コードを呼び出し、実行を照会することができます、 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)メソッドです。|  
|SCRIPTSTATE_STARTED|コードを実行できるスクリプトによって追加されたオブジェクトのイベントをシンクはありませんが、 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)メソッドです。|  
|SCRIPTSTATE_CONNECTED|スクリプトが読み込まれ、イベントをシンクのために接続されます。|  
|SCRIPTSTATE_DISCONNECTED|スクリプトが読み込まれると、実行時の実行状態がイベントをシンクから一時的に切断されています。|  
|SCRIPTSTATE_CLOSED|スクリプトが閉じられました。 スクリプト エンジンは動作しなくなり、ほとんどのメソッドに対してエラーを返します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプトの定数、列挙型、およびエラー コード](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)