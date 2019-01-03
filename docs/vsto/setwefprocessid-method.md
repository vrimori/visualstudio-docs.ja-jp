---
title: SetWefProcessId メソッド
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3ccce49992073f11245929bf7af0b966537bd079
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886151"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId メソッド
  Web 拡張機能フレームワーク (WEF) コンテンツを実行しているプロセス id を提供します。  
  
## <a name="syntax"></a>構文  
  
```csharp  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*dwProcessId*|WEF コンテンツを実行するために使用するプロセスの識別子です。|  
  
## <a name="return-value"></a>戻り値  
 メソッドが正常に完了したかどうかを示す HRESULT 値。  
  
## <a name="remarks"></a>Remarks  
 WEF content のプロセスの作成後が WEF コンテンツを実行する前に、このメソッドを呼び出す必要があります。  
  
 開発環境を WEF content のプロセスにデバッガーをアタッチする場合は、環境は、このメソッドの実装でこの操作を実行する必要があります。  
