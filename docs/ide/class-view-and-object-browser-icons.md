---
title: "[クラス ビュー] ウィンドウとオブジェクト ブラウザーのアイコン | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b6fad74a71e457759bc6b35ecb4679c3f26011e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="class-view-and-object-browser-icons"></a>[クラス ビュー] ウィンドウとオブジェクト ブラウザーのアイコン
**[クラス ビュー]** および**オブジェクト ブラウザー**には、名前空間、クラス、関数、変数などのコード エンティティを表すアイコンが表示されます。 各アイコンおよびその説明を次の表に示します。  
  
|アイコン|説明|アイコン|説明|  
|----------|-----------------|----------|-----------------|  
|![名前空間シンボル](../ide/media/vxnamespace_icon.gif "vxNamespace_Icon")|名前空間|![宣言シンボル](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|メソッドまたは関数|  
|![クラス アイコン](../ide/media/vxclass_icon.gif "vxClass_Icon")|クラス|![演算子シンボル](../ide/media/vxoperator_icon.gif "vxOperator_Icon")|演算子|  
|![ロリポップ インターフェイス シンボル](../ide/media/vxinterface_icon.gif "vxInterface_Icon")|インターフェイス|![プロパティ シンボル](../ide/media/vxproperty_icon.gif "vxProperty_Icon")|プロパティ|  
|![構造体シンボル](../ide/media/vxstruct_icon.gif "vxStruct_Icon")|構造体|![フィールド アイコン](../ide/media/vxfield_icon.gif "vxField_Icon")|フィールドまたは変数|  
|![和集合シンボル](../ide/media/vxunion_icon.gif "vxUnion_Icon")|和集合|![イベント シンボル](../ide/media/vxevent_icon.gif "vxEvent_Icon")|イベント|  
|![列挙型シンボル](../ide/media/vxenum_icon.gif "vxEnum_Icon")|Enum|![定数アイコン](../ide/media/vxconstant_icon.gif "vxConstant_Icon")|定数|  
|![型定義シンボル](../ide/media/vxtypedef_icon.gif "vxTypeDef_Icon")|TypeDef|![列挙型項目シンボル](../ide/media/vxenumitem_icon.gif "vxEnum_Icon")|列挙型項目|  
|![Visual Studio モジュール シンボル](../ide/media/vxmodule_icon.gif "vxModule_Icon")|モジュール|![マップ項目シンボル](../ide/media/vxmapitem_icon.gif "vxMapItem_Icon")|マップ項目|  
|![拡張メソッド シンボル](../ide/media/extensionmethod.gif "ExtensionMethod")|拡張メソッド|![宣言シンボル](../ide/media/vxmethod_icon.gif "vxMethod_Icon")|外部宣言|  
|![デリゲート シンボル](../ide/media/vxdelegate_icon.gif "vxDelegate_Icon")|Delegate|![クラス ビューおよびオブジェクト ブラウザーのエラー アイコン](../ide/media/erroricon.gif "ErrorIcon")|エラー|  
|![例外シンボル](../ide/media/vxexception_icon.gif "vxException_Icon")|例外|![テンプレート シンボル](../ide/media/vxtemplate_icon.gif "vxTemplate_Icon")|テンプレート|  
|![マップ シンボル](../ide/media/vxmap_icon.gif "vxMap_Icon")|マップ|![エラー感嘆符シンボル](../ide/media/vxerror_icon.gif "vxError_Icon")|不明|  
|![型の転送シンボル](../ide/media/ob_type_forward.gif "ob_type_forward")|型の転送|||  
  
## <a name="signal-icons"></a>シグナル アイコン  
 次のシグナル アイコンは、上記のアイコンすべてに適用され、そのアクセシビリティを示します。  
  
> [!NOTE]
>  プロジェクトがソース管理データベースに含まれている場合は、ソース管理のステータス (チェックインまたはチェックアウトなど) を示すシグナル アイコンが追加で表示されることがあります。  
  
|アイコン|説明|  
|----------|-----------------|  
|\<シグナル アイコンなし>|パブリック。 このコンポーネント内のどこからでも、また、それを参照するどのコンポーネントからでもアクセスできます。|  
|![シグナル プロテクト シンボル](../ide/media/vxsignal_icon_key.gif "vxSignal_Icon_Key")|プロテクト。 包含クラスまたは型、あるいは包含クラスまたは型から派生したクラスまたは型からアクセスできます。|  
|![シグナル プライベート シンボル](../ide/media/vxsignal_icon_lock.gif "vxSignal_Icon_Lock")|プライベート。 包含クラスまたは型でのみアクセスできます。|  
|![シグナル シール シンボル](../ide/media/vxsignal_icon_envelope.gif "vxSignal_Icon_Envelope")|シール。|  
|![シグナル フレンド&#47;内部シンボル](../ide/media/vxsignal_icon_diamond.gif "vxSignal_Icon_Diamond")|フレンド/内部。 プロジェクトからのみアクセスできます。|  
|![シグナル アイコン矢印](../ide/media/vxsignal_icon_arrow.gif "vxSignal_Icon_Arrow")|ショートカット。 オブジェクトへのショートカットです。|  
  
## <a name="see-also"></a>関連項目  
 [コードの構造の表示](../ide/viewing-the-structure-of-code.md)