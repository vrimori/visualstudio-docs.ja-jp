---
title: "IActiveScript::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Clone"
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::Clone
現在のスレッドでサイトを持たない読み込まれたスクリプト エンジンが返す現在のスクリプト エンジン \(すべての現在の実行状態プラス\) 複製します。  この新しいスクリプト エンジンのプロパティは元のスクリプト エンジンが初期化された状態への遷移のプロパティと同じです。  
  
## 構文  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### パラメーター  
 `ppscript`  
 \[入力\]複製されたスクリプト エンジンの [IActiveScript](../../winscript/reference/iactivescript.md) のインターフェイスへのポインターを受け取る変数のアドレス。  ホストは、初期化、および使用できる状態になる前にサイトを作成し、新しいスクリプト エンジンの [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) のメソッドを呼び出す必要があります。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されていません\)。|  
  
## 解説  
 `IActiveScript::Clone` のメソッドは `IPersist*::Save`、`CoCreateInstance`と `IPersist*::Load`最適化のため、元のスクリプト エンジンの状態は、新しいスクリプト エンジンに保存され、読み込まれたときに、新しいスクリプト エンジンの状態はと同じです。  の項目は複製されたスクリプト エンジンにレプリケートされますが、項目ごとに特定のオブジェクトのポインターは [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) のメソッドと忘れられ、派生します。  これは、スレッドのエントリ ポイント \(アパートメント モデル\) を持つ同一のオブジェクト モデルを使用するようにします。  
  
 このメソッドは同じスクリプトの複数のインスタンスを実行できるマルチスレッド サーバー ホストに使用されます。  スクリプト エンジンは、ホストが永続的な状態を複製し、`IPersist*` のインターフェイスを持つスクリプト エンジンの新しいインスタンスを作成することによって、同じ結果を達成できます `E_NOTIMPL`を返す場合があります。  
  
 このメソッドは、ベースの呼び出しによりオブジェクトをホストするまたは [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) のインターフェイスに非ベースのスレッドから外部に呼び出すことができます。  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)