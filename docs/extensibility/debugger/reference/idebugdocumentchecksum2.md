---
title: IDebugDocumentChecksum2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 068447399a8cfd43cb5fe07ea82e7cf4400f460c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106719"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
デバッグ ドキュメントのチェックサムを表し、コンポーネント間で、チェックサムをやり取りできるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスを公開するすべてのコンポーネントで実装することができます、 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)インターフェイスです。 ただし、主に実装するもののデバッグ エンジン シンボル ファイル (*.pdb) に埋め込まれているチェックサムは、IDE に戻されますしたり、ソースを検索するときに使用できるようにします。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugDocumentChecksum2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|使用するバイトの最大数を指定されたドキュメントのチェックサムおよびアルゴリズム識別子を取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll