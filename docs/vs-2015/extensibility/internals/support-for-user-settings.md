---
title: ユーザー設定のサポート |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12200fcee084a58520047ca4731dbcc1ed1b4ed4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548667"
---
# <a name="support-for-user-settings"></a>ユーザー設定のサポート
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ユーザー設定のサポート](https://docs.microsoft.com/visualstudio/extensibility/internals/support-for-user-settings)します。  
  
VSPackage は、ユーザーが選択したときに永続化状態変数のグループが 1 つまたは複数の設定カテゴリを定義できます、**設定のインポート/エクスポート**コマンドを**ツール**メニュー。 この永続化を有効にするには、Api の設定を使用するには[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]します。  
  
 カスタム設定ポイントと GUID として参照されるレジストリ エントリは、VSPackage のカテゴリの設定を定義します。 VSPackage が複数のカテゴリの設定をサポートできますが、カスタム設定ポイントによって定義されている各。  
  
-   相互運用機能アセンブリに基づく設定の実装 (を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>インターフェイス)、レジストリを編集するか、レジストラー スクリプト (.rgs ファイル) を使用してカスタム設定ポイントを作成する必要があります。 詳細については、次を参照してください。 [Creating Registrar Scripts](http://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35)します。  
  
-   管理パッケージ フレームワーク (MPF) を使用するコードは、アタッチすることでのカスタム設定ポイントを作成する必要があります、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>各カスタム設定ポイントの VSPackage にします。  
  
     単一 VSPackage は、いくつかのカスタム設定ポイントをサポートしている場合は、各カスタム設定ポイントが別のクラスによって実装されるの一意のインスタンスで登録されますが、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラス。 そのため、クラスの実装設定では、1 つ以上のカテゴリの設定をサポートできます。  
  
## <a name="custom-settings-point-registry-entry-details"></a>カスタム設定ポイントのレジストリ エントリの詳細  
 次の場所にレジストリ エントリでのカスタム設定ポイントが作成されます: hklm \software\microsoft\visualstudio\\*\<バージョン >* \UserSettings\\`<CSPName>`ここで、`<CSPName>` VSPackage のサポートは、カスタム設定ポイントの名前と*\<バージョン >* のバージョンは、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]8.0 などの。  
  
> [!NOTE]
>  Hkey_local_machine \software\microsoft\visualstudio のルート パス\\*\<バージョン >* 代替で上書きすることができる場合にルート、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]統合開発環境 (IDE) です初期化されます。 詳細については、次を参照してください。[コマンド ライン スイッチ](../../extensibility/command-line-switches-visual-studio-sdk.md)します。  
  
 レジストリ エントリの構造は、次に示します。  
  
 Hklm \software\microsoft\visualstudio\\*\<バージョン >* \UserSettings\  
  
 `<CSPName`> = '#12345' s  
  
 パッケージ ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}' を =  
  
 カテゴリ ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY}' を =  
  
 ResourcePackage ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}' を =  
  
 AlternateParent CategoryName を =  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|(既定)|REG_SZ|カスタム設定ポイントの名前|キーの名前、 `<CSPName`>、カスタム設定ポイントのローカライズされていない名前を指定します。<br /><br /> MPF に基づいた実装では、キーの名前を取得するのと組み合わせることで、`categoryName`と`objectName`の引数、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>コンス トラクターに`categoryName_objectName`します。<br /><br /> キーは、空にできます。 またはサテライト DLL にローカライズされた文字列への参照 ID を含めることができます。 この値は、`objectNameResourceID`への引数、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>コンス トラクター。|  
|Package|REG_SZ|GUID|カスタム設定ポイントを実装する VSPackage の GUID です。<br /><br /> 実装で、MPF を使用してに基づいて、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラスを使用して、コンス トラクターの`objectType`引数を含む VSPackage の<xref:System.Type>とリフレクションはこの値を取得します。|  
|カテゴリ|REG_SZ|GUID|設定カテゴリを識別する GUID。<br /><br /> 相互運用機能アセンブリに基づく実装では、この値は任意に選択したは、GUID を[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE に渡します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>メソッド。 これら 2 つのメソッドのすべての実装では、その GUID 引数を確認してください。<br /><br /> MPF に基づいた実装では、この GUID を取得するので、<xref:System.Type>実装するクラスの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]設定メカニズム。|  
|ResourcePackage|REG_SZ|GUID|任意。<br /><br /> サテライト DLL を含むへのパスでは、実装する VSPackage がそれらを指定しない場合、文字列がローカライズされました。<br /><br /> MPF リフレクションを使用して、適切なリソース、VSPackage を取得するため、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラスは、この引数を設定しません。|  
|AlternateParent|REG_SZ|このカスタム設定ポイントを格納しているツール オプション ページの下のフォルダーの名前です。|任意。<br /><br /> 設定の実装をサポートしている場合にのみ、この値を設定する必要があります**ツール オプション**で永続化メカニズムを使用するページ、[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]オートメーション モデルの状態を保存するメカニズムではなく。<br /><br /> AlternateParent キーの値は、このような場合、`topic`のセクション、`topic.sub-topic`特定を識別するために使用される文字列**制御**ページ。 たとえば、**制御**ページ`"TextEditor.Basic"`AlternateParent の値になります。`"TextEditor"`します。<br /><br /> ときに<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>カスタム設定ポイントを生成します。 これは、カテゴリ名と同じです。|

