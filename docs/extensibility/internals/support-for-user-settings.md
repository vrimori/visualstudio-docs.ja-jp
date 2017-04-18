---
title: "ユーザー設定のサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 24bd28ad78f1cd3a21167215ed8348dc79edce6b
ms.lasthandoff: 04/05/2017

---
# <a name="support-for-user-settings"></a>ユーザー設定のサポート
VSPackage は、ユーザーが選択したときに永続化状態変数のグループは、1 つまたは複数の設定カテゴリを定義する可能性があります、**設定のインポート/エクスポート**コマンドを**ツール**メニュー。 この永続化を有効にする設定を使用して Api で、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]です。  
  
 カスタム設定ポイントおよび GUID として参照されているレジストリ エントリは、VSPackage のカテゴリの設定を定義します。 VSPackage は、複数の設定のカテゴリをサポートできますが、カスタム設定ポイントによって定義された各します。  
  
-   相互運用機能アセンブリに基づく設定の実装 (を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>インターフェイス)、レジストリを編集するか、レジストラー スクリプト (.rgs ファイル) を使用してカスタム設定ポイントを作成する必要があります</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>。 詳細については、次を参照してください。[レジストラー スクリプトの作成](/cpp/atl/creating-registrar-scripts)です。  
  
-   Managed Package Framework (MPF) を使用するコードはアタッチしてカスタム設定ポイントを作成する必要があります、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>各カスタム設定ポイントの VSPackage にします</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。  
  
     各カスタム設定ポイントは別のクラスによって実装され、それぞれが固有の<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラス</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>のインスタンスで登録されている 1 つの VSPackage では、いくつかのカスタム設定ポイントをサポートする場合 そのため、実装するクラスの設定は、1 つ以上のカテゴリの設定をサポートできます。  
  
## <a name="custom-settings-point-registry-entry-details"></a>カスタム設定ポイントのレジストリ エントリの詳細  
 次の場所にレジストリ エントリでのカスタム設定ポイントが作成されます: HKLM\Software\Microsoft\VisualStudio\\*\<バージョン >*\UserSettings\\`<CSPName>`ここで、 `<CSPName>` 、VSPackage がサポートする、カスタム設定ポイントの名前と*\<バージョン >*のバージョンは、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]8.0 などのです。  
  
> [!NOTE]
>  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio のルート パス\\*\<バージョン >*代替で上書きすることができる場合のルート、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) を初期化します。 詳細については、次を参照してください。[コマンド ライン スイッチ](../../extensibility/command-line-switches-visual-studio-sdk.md)です。  
  
 レジストリ エントリの構造は、次に示します。  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<バージョン >*\UserSettings\  
  
 `<CSPName`> s '#12345' を =  
  
 パッケージ ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}' を =  
  
 カテゴリ ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY}' を =  
  
 ResourcePackage ' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}' を =  
  
 AlternateParent CategoryName を =  
  
|名前|型|データ|説明|  
|----------|----------|----------|-----------------|  
|(既定)|REG_SZ|カスタム設定ポイントの名前|キーの名前、 `<CSPName`>、カスタム設定ポイントのローカライズされていない名前を指定します。<br /><br /> MPF に基づいて実装では、キーの名前を取得組み合わせることによって、`categoryName`と`objectName`の引数、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>コンス トラクターに`categoryName_objectName`</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。<br /><br /> キーを空にすることや、サテライト DLL にローカライズされた文字列に参照 ID を含めることができます。 この値を取得、`objectNameResourceID`への引数、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>コンス トラクター</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 。|  
|パッケージ|REG_SZ|GUID|カスタム設定ポイントを実装する VSPackage の GUID です。<br /><br /> 実装が MPF を使用してに基づいて、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラス、コンス トラクターの使用`objectType`VSPackage を含む引数<xref:System.Type>し、この値を取得するためにリフレクション</xref:System.Type></xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。|  
|カテゴリ|REG_SZ|GUID|設定のカテゴリを識別する GUID。<br /><br /> 相互運用機能アセンブリに基づく実装では、この値を任意に選択に使用できます、GUID が、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE に渡します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>および<xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>メソッド</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>。 これら 2 つのメソッドのすべての実装では、その引数として GUID を確認してください。<br /><br /> MPF に基づいて実装では、この GUID を取得して、<xref:System.Type>実装するクラスの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]設定メカニズム</xref:System.Type>。|  
|ResourcePackage|REG_SZ|GUID|省略可能です。<br /><br /> サテライト DLL を含むへのパスは、実装する VSPackage がそれらを指定しない場合、文字列をローカライズします。<br /><br /> MPF リフレクションを使用して、適切なリソース、VSPackage を取得するため、<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラスは、この引数を設定しません</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。|  
|AlternateParent|REG_SZ|このカスタム設定ポイントを含むツール オプション ページの下のフォルダーの名前です。|省略可能です。<br /><br /> 設定の実装をサポートしている場合にのみ、この値を設定する必要があります**ツール オプション**で永続化メカニズムを使用しているページ、[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]オートメーション モデル状態を保存するメカニズムではなくです。<br /><br /> AlternateParent キーの値は、このような場合、`topic`のセクションで、`topic.sub-topic`特定の識別に使用される文字列**制御**ページ。 たとえば、**制御**ページ`"TextEditor.Basic"`AlternateParent の値になります`"TextEditor"`です。<br /><br /> ときに<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>、カスタム設定ポイントが生成されますが、カテゴリ名と同じです</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。|
