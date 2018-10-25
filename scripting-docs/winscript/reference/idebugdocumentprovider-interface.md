---
title: IDebugDocumentProvider インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d775deb153205d0e9a452775272285c67e74a210
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949865"
---
# <a name="idebugdocumentprovider-interface"></a>IDebugDocumentProvider インターフェイス
必要に応じてドキュメントをインスタンス化するための手段を提供します。  
  
## <a name="remarks"></a>Remarks  
 ドキュメントをインスタンス化するためのこの間接的な手段:  
  
- により、ドキュメントを読み込む必要がある場合。  
  
- デバッガー IDE 内に含まれるドキュメント オブジェクトを使用します。  
  
- 同じドキュメント オブジェクトにアクセスする複数の方法を使用できます。  
  
  これは効果的に、そのプロバイダーからドキュメントを分離し、プロバイダーは、追加の実行時に、コンテキスト情報を含めることができます。  
  
  継承されたメソッドだけでなく`IDebugDocumentInfo`、`IDebugDocumentProvider`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|既に存在しない場合はインスタンス化するためにドキュメントをによりします。|