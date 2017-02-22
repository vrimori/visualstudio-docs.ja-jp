---
title: "IDiaEnumSegments | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSegments インターフェイス"
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

データ ソースに含まれるさまざまなセグメントを列挙します。  
  
## 構文  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## Vtable の順序でメソッド  
 次の表は `IDiaEnumSegments` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[IDiaEnumSegments::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|この列挙子の [IEnumVARIANT Interface](http://msdn.microsoft.com/ja-jp/139e3c93-faef-4003-9079-e0e94494db3e) のバージョンを取得します。|  
|[IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|線分の数を取得します。|  
|[IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)|インデックスでセグメントを取得します。|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|列挙体シーケンス内の指定のセグメント数を取得します。|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|列挙体シーケンス内の指定した数のセグメントをスキップします。|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|列挙体シーケンスを先頭にリセットします。|  
|[IDiaEnumSegments::Clone](../Topic/IDiaEnumSegments::Clone.md)|現在の列挙子と同じ列挙状態を含む列挙子を作成します。|  
  
## 解説  
  
## 呼び出し元のメモ  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md) のオブジェクトの `QueryInterface` のメソッドを呼び出してこのインターフェイスを取得します。  詳細についてはの例を参照してください。  
  
## 使用例  
 この例ではテーブルの `IDiaEnumSections` のインターフェイスを取得する方法を示します。  セグメントを使用するコード例については[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) のインターフェイスを参照してください。  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                __uuidof( IDiaEnumSegments ),  
                                (void**)&pSegments )  
                  )  
       )  
    {  
        // Do something with this enumeration  
    }  
}  
```  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia80.dll  
  
## 参照  
 [インターフェイス \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)