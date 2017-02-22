---
title: "IDebugProperty2::EnumChildren | Microsoft Docs"
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
  - "IDebugProperty2::EnumChildren"
helpviewer_keywords: 
  - "IDebugProperty2::EnumChildren"
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロパティの子のリストを取得します。  
  
## 構文  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```c#  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### パラメーター  
 `dwFields`  
 \[入力\] [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) の列挙された構造体のフィールドが設定方法を指定する [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) の列挙体のフラグの組み合わせ。  
  
 `dwRadix`  
 \[入力\] 情報を数値書式設定に使用する方法を指定します。  
  
 `guidFilter`  
 \[入力\] 選択するために `DEBUG_PROPERTY_INFO` の列挙子を `dwAttribFilter` すると `pszNameFilter` のパラメーターで使用されるフィルターの GUID。  たとえばローカル変数の `guidFilterLocals` のフィルター。  
  
 `dwAttribFilter`  
 \[出力\] 列挙するオブジェクトの種類をこのプロパティの子である可能性のあるすべてのメソッドについてたとえば `DBG_ATTRIB_METHOD` 指定する [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) の列挙体のフラグの組み合わせ。  `guidFilter` と `pszNameFilter` のパラメーターと組み合わせて使用します。  
  
 `pszNameFilter`  
 \[入力\] 選択するために `DEBUG_PROPERTY_INFO` の列挙子を `guidFilter` すると `dwAttribFilter` のパラメーターで使用されるフィルターの名前。  たとえばこのパラメーターを MyX 「」に設定するとフィルター処理「 MyX を持つすべての子に」  
  
 `dwTimeout`  
 \[出力\] このメソッドから制御が戻るまで待機するミリ秒単位の最大時間を指定します。  無期限に待機するために `INFINITE` を使用します。  
  
 `ppEnum`  
 \[入力\] [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) の子オブジェクトを含むプロパティのリストを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  
  
## 参照  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP\_INFO\_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG\_ATTRIB\_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)