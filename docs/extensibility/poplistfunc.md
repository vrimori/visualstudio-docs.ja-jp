---
title: POPLISTFUNC |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 950807b0568a28763b369fef4041c69b264d12fc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138565"
---
# <a name="poplistfunc"></a>POPLISTFUNC
このコールバックに用意されて、 [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE によってファイルまたはディレクトリの一覧を更新する、ソース管理プラグインによって使用されます (に指定されている、`SccPopulateList`関数)。  
  
 ユーザーが選択すると、**取得**IDE では、コマンドのすべてのファイルのユーザー得ることができるリスト ボックスが表示されます。 残念ながら、IDE が認識していないユーザーが取得可能性があります。 すべてのファイルの正確な一覧のみプラグインにはこの一覧を示します。 他のユーザーをソース コード管理プロジェクト ファイルに追加した場合は、一覧で、これらのファイルが表示されますが、IDE が認識していないこと。 IDE では、ユーザーが取得できると思われるファイルの一覧を構築します。 呼び出しをユーザーには、この一覧が表示されます、前に、 [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,`ソース管理プラグインの提供を追加して、一覧からファイルを削除できます。  
  
## <a name="signature"></a>署名  
 ソース管理プラグインは、次のプロトタイプで、IDE 実装関数を呼び出すことによって、リストを変更します。  
  
```cpp  
typedef BOOL (*POPLISTFUNC) (  
   LPVOID pvCallerData,  
   BOOL fAddRemove,  
   LONG nStatus,  
   LPSTR lpFileName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 pvCallerData  
 `pvCallerData`に呼び出し元 (IDE) によって渡されたパラメーター、 [SccPopulateList](../extensibility/sccpopulatelist-function.md)です。 ソース管理プラグインは、このパラメーターの内容について何も想定してください。  
  
 fAddRemove  
 場合`TRUE`、`lpFileName`ファイル、ファイルの一覧に追加する必要があります。 場合`FALSE`、`lpFileName`ファイル、ファイルの一覧から削除する必要があります。  
  
 送ら  
 ステータス`lpFileName`(の組み合わせ、`SCC_STATUS`ビット; 参照してください[ファイル ステータス コード](../extensibility/file-status-code-enumerator.md)詳細)。  
  
 lpFileName  
 ディレクトリの完全パスを追加または一覧から削除するファイル名。  
  
## <a name="return-value"></a>戻り値  
  
|[値]|説明|  
|-----------|-----------------|  
|`TRUE`|プラグインを続行できますこの関数を呼び出します。|  
|`FALSE`|(メモリ不足) などの IDE 側で問題が発生しました。 操作は、プラグインの場合に中断する必要があります。|  
  
## <a name="remarks"></a>コメント  
 渡して、この関数を呼び出しますが、ソース管理プラグインを追加したり、ファイルの一覧から削除する必要があるファイルごとに、`lpFileName`です。 `fAddRemove`フラグは、一覧に追加する新しいファイルや古いファイルを削除することを示します。 `nStatus`パラメーターは、ファイルの状態。 SCC プラグインを追加して、ファイルの削除が完了したらからが返されます、 [SccPopulateList](../extensibility/sccpopulatelist-function.md)呼び出します。  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST`機能ビットは Visual Studio に必要です。  
  
## <a name="see-also"></a>関連項目  
 [IDE によって実装されているコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)