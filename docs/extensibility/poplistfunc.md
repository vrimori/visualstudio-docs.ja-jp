---
title: "POPLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPDIRLISTFUNC"
helpviewer_keywords: 
  - "POPLISTFUNC コールバック関数"
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# POPLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このコールバックが提供される、 [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE でファイルまたはディレクトリの一覧を更新する、ソース管理プラグインによって使用されます \(に指定されている、 `SccPopulateList` 関数\)。  
  
 ユーザーが選択すると、 **取得** IDE では、コマンドのユーザーを取得できるすべてのファイルの一覧ボックスが表示されます。 残念ながら、IDE を知らないユーザーを取得可能性があります。 すべてのファイルの正確な一覧このリスト プラグインのみがあります。 他のユーザーをソース コード管理プロジェクト ファイルに追加した場合は、これらのファイルが、一覧に表示する必要がありますが、IDE が認識していないこと。 IDE では、ユーザーを取得できると思われるファイルの一覧を作成します。 呼び出しをユーザーにこの一覧を表示にする前に、 [SccPopulateList](../extensibility/sccpopulatelist-function.md)`,` 、ソース管理プラグインを与えるを追加し、一覧からファイルを削除します。  
  
## Signature  
 ソース管理プラグインでは、次のプロトタイプで IDE 実装関数を呼び出してでリストを変更します。  
  
```cpp#  
typedef BOOL (*POPLISTFUNC) ( LPVOID pvCallerData, BOOL fAddRemove, LONG nStatus, LPSTR lpFileName );  
```  
  
## パラメーター  
 pvCallerData  
 `pvCallerData` に呼び出し元 \(IDE\) で渡されるパラメーター、 [SccPopulateList](../extensibility/sccpopulatelist-function.md)です。 ソース管理プラグインは、このパラメーターの内容について何も想定してください。  
  
 fAddRemove  
 場合 `TRUE`, 、`lpFileName` ファイル、ファイルの一覧に追加する必要があります。 場合 `FALSE`, 、`lpFileName` ファイルで、ファイルの一覧から削除する必要があります。  
  
 送ら  
 ステータス `lpFileName` \(の組み合わせ、 `SCC_STATUS` ビット; を参照してください [ファイルの状態コード](../extensibility/file-status-code-enumerator.md) 詳細\)。  
  
 lpFileName  
 一覧から追加または削除するには、ファイル名の完全なディレクトリ パス。  
  
## 戻り値  
  
|値|説明|  
|-------|--------|  
|`TRUE`|プラグインを続行できますこの関数を呼び出します。|  
|`FALSE`|\(メモリの状況の送信\) などの IDE 側で問題が発生しました。 操作は、プラグインの場合に中断する必要があります。|  
  
## 解説  
 ソース管理プラグインを追加したり、ファイルの一覧から削除する必要のある各ファイルにするのに対してを渡して、この関数を呼び出し、 `lpFileName`です。`fAddRemove` フラグは、一覧に追加する新しいファイルまたは古いファイルを削除することを示します。`nStatus` パラメーターは、ファイルの状態。 プラグインのソース コード管理を追加して、ファイルの削除が完了したらからが返されます、 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 呼び出します。  
  
> [!NOTE]
>  `SCC_CAP_POPULATELIST` 機能ビットは、Visual Studio に必要です。  
  
## 参照  
 [IDE で実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)   
 [ファイルの状態コード](../extensibility/file-status-code-enumerator.md)