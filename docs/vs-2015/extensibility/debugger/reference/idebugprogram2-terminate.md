---
title: IDebugProgram2::Terminate |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15dcab4ac15a8059d9ca569478957c3a66e277d3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906159"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

プログラムを終了します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 可能であれば、プログラムは終了し、プロセスからアンロードそれ以外の場合、デバッグ エンジン (DE) は、必要なクリーンアップを実行します。  
  
 このメソッドまたは[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)メソッドはすべてのデバッグを停止するユーザーへの応答では通常、IDE によって呼び出されます。 このメソッドの実装では、プロセス内でプログラムを終了する必要があります、理想的には、します。 それができない場合、DE する必要がありますプログラムがこのプロセスではこれ以上実行されないように (および必要なクリーンアップを行います)。 場合、`IDebugProcess2::Terminate`メソッドは、IDE によって呼び出された、プロセス全体は終了されてからしばらく、`IDebugProgram2::Terminate`メソッドが呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)

