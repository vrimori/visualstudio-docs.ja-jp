---
title: ユーザー設定のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cf2ba79cc8bff57de1fd410f8a2780825d693181
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-user-settings"></a>ユーザー設定のサポート
VSPackage は、ユーザーが選択したときに永続化状態変数のグループ、1 つまたは複数の設定カテゴリの定義可能性があります、**設定のインポート/エクスポート**コマンドを**ツール**メニュー。 この永続化を有効にする設定を使用して Api で、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]です。  
  
 カスタム設定ポイントおよび GUID として参照されているレジストリ エントリは、VSPackage のカテゴリの設定を定義します。 VSPackage は、複数の設定のカテゴリをサポートできますが、カスタム設定ポイントによって定義された各します。  
  
-   相互運用機能アセンブリに基づく設定の実装 (を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>インターフェイス)、レジストリを編集するか、レジストラー スクリプト (.rgs ファイル) を使用してカスタム設定ポイントを作成する必要があります。 詳細については、次を参照してください。[レジストラー スクリプトの作成](/cpp/atl/creating-registrar-scripts)です。  
  
-   Managed Package Framework (MPF) を使用するコードはアタッチしてカスタム設定ポイントを作成する必要があります、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>各カスタム設定ポイントの VSPackage にします。  
  
     1 つの VSPackage は、いくつかのカスタム設定ポイントをサポートしている、各カスタム設定ポイントは別のクラスによって実装およびの一意のインスタンスでそれぞれが登録されている場合、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラスです。 そのため、実装するクラスの設定は、1 つ以上のカテゴリの設定をサポートできます。  
  
## <a name="custom-settings-point-registry-entry-details"></a>カスタム設定ポイントのレジストリ エントリの詳細  
 次の場所にレジストリ エントリでのカスタム設定ポイントが作成されます: HKLM\Software\Microsoft\VisualStudio\\*\<バージョン >*\UserSettings\\`<CSPName>`ここで、`<CSPName>` 、VSPackage がサポートする、カスタム設定ポイントの名前と*\<バージョン >*のバージョンは、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]8.0 などのです。  
  
> [!NOTE]
>  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio のルート パス\\*\<バージョン >*代替でオーバーライドできるルートの場合、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です初期化されます。 詳細については、次を参照してください。[コマンド ライン スイッチ](../../extensibility/command-line-switches-visual-studio-sdk.md)です。  
  
 レジストリ エントリの構造は、次に示します。  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<バージョン >*\UserSettings\  
  
 `<CSPName`> = '#12345' s  
  
 パッケージ ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}' を =  
  
 カテゴリ ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY}' を =  
  
 ResourcePackage ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}' を =  
  
 AlternateParent CategoryName を =  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|(既定)|REG_SZ|カスタム設定ポイントの名前|キーの名前、 `<CSPName`>、カスタム設定ポイントのローカライズされていない名前を指定します。<br /><br /> MPF に基づいて実装では、キーの名前を取得組み合わせることによって、`categoryName`と`objectName`の引数、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>にコンス トラクター`categoryName_objectName`です。<br /><br /> キーを空にすることや、サテライト DLL にローカライズされた文字列に参照 ID を含めることができます。 この値は、`objectNameResourceID`への引数、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>コンス トラクターです。|  
|Package|REG_SZ|GUID|カスタム設定ポイントを実装する VSPackage の GUID です。<br /><br /> 実装が MPF を使用してに基づいて、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラス、コンス トラクターの使用`objectType`VSPackage を含む引数<xref:System.Type>し、この値を取得するためにリフレクションします。|  
|カテゴリ|REG_SZ|GUID|設定のカテゴリを識別する GUID。<br /><br /> 相互運用機能アセンブリに基づく実装では、この値を任意に選択したにすることができます、GUID を[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE に渡します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>メソッドです。 これら 2 つのメソッドのすべての実装では、その引数として GUID を確認してください。<br /><br /> MPF に基づいて実装では、この GUID を取得して、<xref:System.Type>実装するクラスの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]設定メカニズムです。|  
|ResourcePackage|REG_SZ|GUID|任意。<br /><br /> サテライト DLL を含むへのパスは、実装する VSPackage がそれらを指定しない場合、文字列をローカライズします。<br /><br /> MPF リフレクションを使用して、適切なリソース、VSPackage を取得するため、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラスは、この引数を設定しません。|  
|AlternateParent|REG_SZ|このカスタム設定ポイントを含むツール オプション ページの下のフォルダーの名前です。|任意。<br /><br /> 設定の実装をサポートしている場合にのみ、この値を設定する必要があります**ツール オプション**で永続化メカニズムを使用しているページ、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]オートメーション モデル状態を保存するメカニズムではなくです。<br /><br /> AlternateParent キーの値は、このような場合、`topic`のセクションで、`topic.sub-topic`特定の識別に使用される文字列**制御**ページ。 たとえば、**制御**ページ`"TextEditor.Basic"`AlternateParent の値になります`"TextEditor"`です。<br /><br /> ときに<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>カスタム設定ポイントが生成されますが、カテゴリ名と同じです。|