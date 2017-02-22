---
title: "[クラス ビュー] ウィンドウとオブジェクト ブラウザーのアイコン | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アイコン、オブジェクト ブラウザー"
  - "シグナル アイコン"
  - "[クラス ビュー] ツール、シンボル"
  - "グラフィック シンボル"
  - "IntelliSense、アイコン"
  - "アイコン、Intellisense"
  - "シンボル、オブジェクト ブラウザー アイコン"
  - "オブジェクト ブラウザー、クラス ビューのアイコン"
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# [クラス ビュー] ウィンドウとオブジェクト ブラウザーのアイコン
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[クラス ビュー\]** および**オブジェクト ブラウザー**には、名前空間、クラス、関数、変数などのコード エンティティを表すアイコンが表示されます。  各アイコンおよびその説明を次の表に示します。  
  
|Icon|Description|Icon|Description|  
|----------|-----------------|----------|-----------------|  
|![名前空間シンボル](../ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|名前空間|![宣言シンボル](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|メソッドまたは関数|  
|![クラス アイコン](../ide/media/vxclass_icon.png "vxClass\_Icon")|Class|![演算子シンボル](../ide/media/vxoperator_icon.png "vxOperator\_Icon")|\[演算子\]|  
|![ロリポップ インターフェイス シンボル](../ide/media/vxinterface_icon.png "vxInterface\_Icon")|Interface|![プロパティ シンボル](../ide/media/vxproperty_icon.png "vxProperty\_Icon")|プロパティ|  
|![構造体シンボル](../ide/media/vxstruct_icon.png "vxStruct\_Icon")|Structure|![フィールド アイコン](../ide/media/vxfield_icon.png "vxField\_Icon")|フィールドまたは変数|  
|![共用体シンボル](../ide/media/vxunion_icon.png "vxUnion\_Icon")|共用体|![イベント シンボル](../ide/media/vxevent_icon.png "vxEvent\_Icon")|Event|  
|![一覧表示シンボル](../ide/media/vxenum_icon.png "vxEnum\_Icon")|Enum|![定数アイコン](../ide/media/vxconstant_icon.png "vxConstant\_Icon")|定数|  
|![型定義シンボル](../ide/media/vxtypedef_icon.png "vxTypeDef\_Icon")|typedef|![項目の一覧表示シンボル](../ide/media/vxenumitem_icon.png "vxEnumItem\_Icon")|列挙型項目|  
|![Visual Studio モジュール シンボル](../ide/media/vxmodule_icon.gif "vxModule\_Icon")|Module|![マップ項目シンボル](../ide/media/vxmapitem_icon.png "vxMapItem\_Icon")|マップ項目|  
|![拡張メソッド シンボル](../ide/media/extensionmethod.png "ExtensionMethod")|拡張メソッド|![宣言シンボル](../ide/media/vxmethod_icon.png "vxMethod\_Icon")|外部宣言|  
|![デリゲート シンボル](../ide/media/vxdelegate_icon.png "vxDelegate\_Icon")|Delegate|![クラス ビューおよびオブジェクト ブラウザーのエラー アイコン](../ide/media/erroricon.png "ErrorIcon")|エラー|  
|![例外シンボル](../ide/media/vxexception_icon.png "vxException\_Icon")|例外|![テンプレート シンボル](../ide/media/vxtemplate_icon.png "vxTemplate\_Icon")|テンプレート|  
|![マップ シンボル](../ide/media/vxmap_icon.png "vxMap\_Icon")|マップ|![エラー感嘆符シンボル](../ide/media/vxerror_icon.png "vxError\_Icon")|Unknown|  
|![型転送シンボル](../ide/media/ob_type_forward.png "ob\_type\_forward")|次の型|||  
  
## シグナル アイコン  
 次のシグナル アイコンは、上記のアイコンすべてに適用され、そのアクセシビリティを示します。  
  
> [!NOTE]
>  プロジェクトがソース管理データベースに格納されている場合は、ソース管理のステータス \(チェックインまたはチェックアウトなど\) を示すシグナル アイコンが追加で表示されることがあります。  
  
|Icon|Description|  
|----------|-----------------|  
|\<シグナル アイコンなし\>|Public  このコンポーネント内のどこからでも、また、それを参照するどのコンポーネントからでもアクセスできます。|  
|![シグナル プロテクト シンボル](../ide/media/vxsignal_icon_key.png "vxSignal\_Icon\_Key")|Protected  包含クラスや包含型、または、包含クラスや包含型から派生したクラスや型からアクセスできます。|  
|![シグナル プライベート シンボル](../ide/media/vxsignal_icon_lock.png "vxSignal\_Icon\_Lock")|プライベート。  包含クラスや包含型の中からだけアクセスできます。|  
|![シグナル シール シンボル](../ide/media/vxsignal_icon_envelope.png "vxSignal\_Icon\_Envelope")|シール。|  
|![シグナル フレンド&#47;内部シンボル](../ide/media/vxsignal_icon_diamond.png "vxSignal\_Icon\_Diamond")|友人および内部。  そのプロジェクトからだけアクセスできます。|  
|![シグナル アイコン矢印](../ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|ショートカット。  オブジェクトへのショートカットです。|  
  
## 参照  
 [コードの構造の表示](../ide/viewing-the-structure-of-code.md)