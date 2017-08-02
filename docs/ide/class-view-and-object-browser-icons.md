---
title: "[クラス ビュー] ウィンドウとオブジェクト ブラウザーのアイコン | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# [クラス ビュー] ウィンドウとオブジェクト ブラウザーのアイコン
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[クラス ビュー\]** および**オブジェクト ブラウザー**には、名前空間、クラス、関数、変数などのコード エンティティを表すアイコンが表示されます。  各アイコンおよびその説明を次の表に示します。  
  
|Icon|Description|Icon|Description|  
|----------|-----------------|----------|-----------------|  
|![名前空間シンボル](~/docs/ide/media/vxnamespace_icon.gif "vxNamespace\_Icon")|名前空間|![宣言シンボル](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|メソッドまたは関数|  
|![クラス アイコン](~/docs/ide/media/vxclass_icon.gif "vxClass\_Icon")|Class|![演算子シンボル](~/docs/ide/media/vxoperator_icon.gif "vxOperator\_Icon")|\[演算子\]|  
|![ロリポップ インターフェイス シンボル](~/docs/ide/media/vxinterface_icon.gif "vxInterface\_Icon")|Interface|![プロパティ シンボル](~/docs/ide/media/vxproperty_icon.gif "vxProperty\_Icon")|プロパティ|  
|![構造体シンボル](~/docs/ide/media/vxstruct_icon.gif "vxStruct\_Icon")|Structure|![フィールド アイコン](~/docs/ide/media/vxfield_icon.gif "vxField\_Icon")|フィールドまたは変数|  
|![共用体シンボル](~/docs/ide/media/vxunion_icon.gif "vxUnion\_Icon")|共用体|![イベント シンボル](~/docs/ide/media/vxevent_icon.gif "vxEvent\_Icon")|Event|  
|![一覧表示シンボル](~/docs/ide/media/vxenum_icon.gif "vxEnum\_Icon")|Enum|![定数アイコン](~/docs/ide/media/vxconstant_icon.gif "vxConstant\_Icon")|定数|  
|![型定義シンボル](~/docs/ide/media/vxtypedef_icon.gif "vxTypeDef\_Icon")|typedef|![項目の一覧表示シンボル](~/docs/ide/media/vxenumitem_icon.gif "vxEnumItem\_Icon")|列挙型項目|  
|![Visual Studio モジュール シンボル](~/docs/ide/media/vxmodule_icon.gif "vxModule\_Icon")|Module|![マップ項目シンボル](~/docs/ide/media/vxmapitem_icon.gif "vxMapItem\_Icon")|マップ項目|  
|![拡張メソッド シンボル](~/docs/ide/media/extensionmethod.gif "ExtensionMethod")|拡張メソッド|![宣言シンボル](~/docs/ide/media/vxmethod_icon.gif "vxMethod\_Icon")|外部宣言|  
|![デリゲート シンボル](~/docs/ide/media/vxdelegate_icon.gif "vxDelegate\_Icon")|Delegate|![クラス ビューおよびオブジェクト ブラウザーのエラー アイコン](~/docs/ide/media/erroricon.gif "ErrorIcon")|エラー|  
|![例外シンボル](~/docs/ide/media/vxexception_icon.gif "vxException\_Icon")|例外|![テンプレート シンボル](~/docs/ide/media/vxtemplate_icon.gif "vxTemplate\_Icon")|テンプレート|  
|![マップ シンボル](~/docs/ide/media/vxmap_icon.gif "vxMap\_Icon")|マップ|![エラー感嘆符シンボル](~/docs/ide/media/vxerror_icon.gif "vxError\_Icon")|Unknown|  
|![型転送シンボル](~/docs/ide/media/ob_type_forward.gif "ob\_type\_forward")|次の型|||  
  
## シグナル アイコン  
 次のシグナル アイコンは、上記のアイコンすべてに適用され、そのアクセシビリティを示します。  
  
> [!NOTE]
>  プロジェクトがソース管理データベースに格納されている場合は、ソース管理のステータス \(チェックインまたはチェックアウトなど\) を示すシグナル アイコンが追加で表示されることがあります。  
  
|Icon|Description|  
|----------|-----------------|  
|\<シグナル アイコンなし\>|Public  このコンポーネント内のどこからでも、また、それを参照するどのコンポーネントからでもアクセスできます。|  
|![シグナル プロテクト シンボル](~/docs/ide/media/vxsignal_icon_key.gif "vxSignal\_Icon\_Key")|Protected  包含クラスや包含型、または、包含クラスや包含型から派生したクラスや型からアクセスできます。|  
|![シグナル プライベート シンボル](~/docs/ide/media/vxsignal_icon_lock.gif "vxSignal\_Icon\_Lock")|プライベート。  包含クラスや包含型の中からだけアクセスできます。|  
|![シグナル シール シンボル](~/docs/ide/media/vxsignal_icon_envelope.gif "vxSignal\_Icon\_Envelope")|シール。|  
|![シグナル フレンド&#47;内部シンボル](~/docs/ide/media/vxsignal_icon_diamond.gif "vxSignal\_Icon\_Diamond")|友人および内部。  そのプロジェクトからだけアクセスできます。|  
|![シグナル アイコン矢印](~/docs/ide/media/vxsignal_icon_arrow.gif "vxSignal\_Icon\_Arrow")|ショートカット。  オブジェクトへのショートカットです。|  
  
## 参照  
 [コードの構造の表示](../ide/viewing-the-structure-of-code.md)