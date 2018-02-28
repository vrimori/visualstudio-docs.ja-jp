---
title: "IDispError インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f139d317db5aa00f03f8e9abd71020e5ff35b03
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idisperror-interface"></a>IDispError インターフェイス
コンテキストの詳細なエラー情報を提供します。  
  
> [!NOTE]
>  このインターフェイスは実装されていません。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDispError`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|特定の種類のエラー情報を取得します。|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|次の取得`IDispError`オブジェクト。|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|エラー コードを取得、`IDispError`オブジェクト。|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|クラスまたはエラーが発生したアプリケーションの言語に依存するプログラム識別子を返します。|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|ヘルプ ファイルのパスと可能な場合、エラーを説明するトピックのコンテキスト ID を返します。|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|エラーの説明テキストを返します。|