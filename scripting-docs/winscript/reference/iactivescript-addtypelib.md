---
title: "IActiveScript::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_AddTypeLib"
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddTypeLib
スクリプトの名前空間にタイプ ライブラリを追加します。  これは、C\/C\+\+ の `#include` ディレクティブに似ています。  これは、一連のクラス定義 `typedefs`、およびスクリプトへの実行時環境で使用できるに追加する名前付き定数などの定義済みの項目ができます。  
  
## 構文  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### パラメーター  
 `guidTypeLib`  
 \[入力\]追加するタイプ ライブラリの CLSID。  
  
 `dwMaj`  
 \[入力\]メジャー バージョン番号。  
  
 `dwMin`  
 \[入力\]マイナー バージョン番号。  
  
 `dwFlags`  
 \[入力\]オプション フラグ。  次は、の場合もあります:  
  
|値|説明|  
|-------|--------|  
|SCRIPTTYPELIB\_ISCONTROL|タイプ ライブラリは、ホストによって使用される ActiveX コントロールについて説明します。|  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されていません\)。|  
|`TYPE_E_CANTLOADLIBRARY`|指定されたタイプ ライブラリを読み込むことができませんでした。|  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)