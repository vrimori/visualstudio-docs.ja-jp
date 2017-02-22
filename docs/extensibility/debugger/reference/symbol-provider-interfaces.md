---
title: "シンボルのプロバイダー インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "シンボル ハンドラーのインターフェイス"
  - "シンボル ハンドラー、インターフェイス"
  - "シンボル ハンドラー、変数の評価"
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# シンボルのプロバイダー インターフェイス
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

次に [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] のインターフェイスを処理するシンボルです。  
  
## 説明  
 これらのインターフェイスは中断モード中に変数の呼び出しのスタックを評価するために使用されます。  これらは共通言語ランタイムのシンボルのプロバイダー \(SP\) にだけ実行されます。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|ストアド プロシージャ|項目のアドレスを表します。|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|ストアド プロシージャ|プロセス ID へのアクセスを提供する項目のアドレスを表します。|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|ストアド プロシージャ|配列のシンボルまたは配列型を表します。|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|ストアド プロシージャ|クラスまたはクラス型のシンボルを表します。|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|ストアド プロシージャ|マネージ コードに固有のメソッドと COM\+ プロバイダーのシンボルを表します。|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|ストアド プロシージャ|COM\+ シンボルのプロバイダーをマネージ コードに固有の **IDebugComPlusSymbolProvider を**  表し拡張メソッドです。|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|ストアド プロシージャ|そのほかのシンボルまたは型のコンテナーである型またはシンボルを表します。|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|ストアド プロシージャ|シンボルにアタッチできるカスタム属性を表します。|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|ストアド プロシージャ|メソッドまたは型のカスタム属性のクエリを表します。|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|ストアド プロシージャ|シンボルはカスタム属性へのアクセスを提供します。|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|ストアド プロシージャ|実行時に判断できる型の基本インターフェイスです。|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|ストアド プロシージャ|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) のオブジェクトの動的フィールドを表します。|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|ストアド プロシージャ|列挙型を表します。|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|ストアド プロシージャ|マネージ コードのジェネリックのサポートに使用可能なフィールドの種類を拡張します。|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|ストアド プロシージャ|すべてのフィールドの基本クラス ; シンボルまたは型の説明を表します。|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|ストアド プロシージャ|マネージ コードのジェネリック型のフィールドの定義を表します。|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|ストアド プロシージャ|マネージ コードのジェネリック型のフィールドのインスタンスを表します。|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|ストアド プロシージャ|マネージ コードのジェネリック型のパラメーターを表します。|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|ストアド プロシージャ|メソッドを表します。|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|ストアド プロシージャ|デバッグのオプション修飾子を表します。|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|ストアド プロシージャ|ポインターを表します。|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|ストアド プロシージャ|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のインターフェイスから基本型の列挙値を表します。|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|ストアド プロシージャ|取得または設定するにはマネージ コード クラスのプロパティを表します。|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|ストアド プロシージャ|シンボルを提供するプロバイダーのシンボルを表します。|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|ストアド プロシージャ|メタデータに直接アクセスとシンボルのプロバイダーを表しコア シンボルはインターフェイスします。|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|ストアド プロシージャ|型を表すフィールドを作成する機能を表します。|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|ストアド プロシージャ|**IDebugTypeFieldBuilder を**  配列型を作成できるように拡張されています。|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|ストアド プロシージャ|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) オブジェクトのコレクションを表します。|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|ストアド プロシージャ|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) オブジェクトのコレクションを表します。|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|ストアド プロシージャ|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) オブジェクトのコレクションを表します。|  
  
## 参照  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)