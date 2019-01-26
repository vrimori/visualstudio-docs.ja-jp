---
title: プロバイダーのインターフェイスのシンボル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 908e597d9ee0a1db4e78de02f3dd4ade1a9aa119
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945360"
---
# <a name="symbol-provider-interfaces"></a>シンボル プロバイダーのインターフェイス
シンボルの処理インターフェイスを次に、[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]します。  
  
## <a name="discussion"></a>説明  
 これらのインターフェイスは、中断モード中に呼び出し履歴内の変数を評価に使用されます。 共通言語ランタイムのシンボル プロバイダー (SP) に対してのみ実装されます。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|項目のアドレスを表します。|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|プロセス ID にアクセスするため、項目のアドレスを表します。|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|シンボルの配列または配列型を表します。|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|クラスのシンボルまたはクラス型を表します。|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|マネージ コードに固有のメソッドで COM + シンボル プロバイダーを表します。|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|マネージ コードに固有のメソッドで COM + シンボル プロバイダーを表し、拡張、 **IDebugComPlusSymbolProvider**します。|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|シンボルまたはその他の記号または型のコンテナーである型を表します。|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|シンボルに関連付けることができるカスタム属性を表します。|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|メソッドまたは型のカスタム属性のクエリを表します。|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|シンボルには、カスタム属性へのアクセスを提供します。|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|実行時に判断できる任意の型の基本インターフェイスです。|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|動的フィールドを表す、 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)オブジェクト。|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|列挙型を表します。|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|sp|マネージ コードのジェネリックをサポートするために使用できるフィールドの型を拡張します。|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|すべてのフィールドの基本クラスシンボルまたは型の記述を表します。|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|マネージ コードのジェネリック型のフィールドの定義を表します。|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|マネージ コードのジェネリック型のフィールドのインスタンスを表します。|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|マネージ コードのジェネリック型のパラメーターを表します。|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|メソッドを表します。|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|デバッグ オプションの修飾子を表します。|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|ポインターを表します。|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|プリミティブ型の列挙値を表す、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)インターフェイス。|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|設定または取得が可能なマネージ コード クラスのプロパティを表します。|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|シンボルよぶ型を提供するシンボル プロバイダーを表します。|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|メタデータとコアのシンボル インターフェイスに直接アクセス権を持つシンボル プロバイダーを表します。|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|型を表すフィールドを作成する機能を表します。|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|拡張、 **IDebugTypeFieldBuilder**配列型を作成できるようにします。|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|コレクションを表します[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)オブジェクト。|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|コレクションを表します[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)オブジェクト。|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|コレクションを表します[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)オブジェクト。|  
  
## <a name="see-also"></a>関連項目  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)