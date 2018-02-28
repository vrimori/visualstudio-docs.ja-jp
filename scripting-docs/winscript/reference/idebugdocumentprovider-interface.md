---
title: "IDebugDocumentProvider インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider インターフェイス
要求時にドキュメントをインスタンス化するための手段を提供します。  
  
## <a name="remarks"></a>コメント  
 ドキュメントをインスタンス化するため間接ことを意味します。  
  
-   必要なときに読み込まれるドキュメントを許可します。  
  
-   デバッガー IDE 内に含まれるドキュメント オブジェクトがします。  
  
-   同じドキュメント オブジェクトにアクセスする複数の方法を使用できます。  
  
 これは実質的に、プロバイダーからドキュメントを分離し、プロバイダーの追加の実行時に、コンテキスト情報を持ちます。  
  
 継承されたメソッドだけでなく`IDebugDocumentInfo`、`IDebugDocumentProvider`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|既に存在しない場合にインスタンス化するドキュメントが発生します。|