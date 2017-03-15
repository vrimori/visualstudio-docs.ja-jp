---
title: "登録と選択 (ソース コントロール VSPackage) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 34
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 693955c38d4d53418a92357e54bfc7c2965bdc3e
ms.lasthandoff: 02/22/2017

---
# <a name="registration-and-selection-source-control-vspackage"></a>登録と (ソース コントロールの vs パッケージ) の選択
公開することを VSPackage を登録する必要があるソース管理、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 1 つ以上のソース管理 VSPackage が登録されている場合、ユーザーは、適切なタイミングで読み込むためにどの VSPackage を選択できます。 参照してください[VSPackages](../../extensibility/internals/vspackages.md) VSPackages およびそれらを登録する方法の詳細についてです。  
  
## <a name="registering-a-source-control-package"></a>ソース管理パッケージを登録します。  
 ソース管理パッケージを登録できるように、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境は、サポートされている機能のおよびクエリを見つけることができます。 これは、ことは、遅延読み込みスキームが必要な機能やコマンド、または明示的に要求された場合にのみのパッケージのインスタンスが作成されます。  
  
 VSPackages \software\microsoft\visualstudio をバージョン固有のレジストリ キーに情報を配置する\\*X.Y*ここで、 *X*メジャー バージョン番号と*Y*マイナー バージョン番号です。 この実習での複数のバージョンのサイド バイ サイド インストールをサポートする機能は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理 VSPackages だけでなく、ユーザー インターフェイス (UI) が複数インストールされているソース管理プラグイン (経由でソース管理アダプター パッケージ) の中から選択をサポートしています。 1 つだけアクティブなソース管理プラグインまたはできます VSPackage 一度に。 ただし、下記のよう IDE では、自動ソリューションに基づくパッケージ スワッピング メカニズムをソース管理プラグインと vspackages にある間の切り替え。 この選択方法を有効にするソース管理 VSPackage 部分に対していくつかの要件があります。  
  
### <a name="registry-entries"></a>レジストリ エントリ  
 ソース管理パッケージには、次の&3; つのプライベート Guid が必要があります。  
  
-   パッケージ GUID: これは、ソース コントロールの実装 (ここでは ID_Package と呼ばれます) を含むパッケージのメインの GUID です。  
  
-   ソース管理 GUID: このソース管理、Visual Studio のソース コントロールのスタブを登録するために使用する VSPackage に guid し、はコマンド UI コンテキスト GUID としても使用します。 ソース コントロール サービス GUID は、ソース管理の GUID が登録されます。 この例では、ソース管理の GUID を ID_SccProvider と呼びます。  
  
-   ソース管理サービスの GUID。 これは、プライベート サービス (ここでは SID_SccPkgService と呼ばれる) Visual Studio によって使用される GUID です。 さらに、ソース管理パッケージが vspackages にある、ツール ウィンドウの他の Guid を定義する必要があります。  
  
 次のレジストリ エントリは、ソース管理 VSPackage で行う必要があります。  
  
|キー名|エントリ|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(既定値) = 対応する rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(既定値) = 対応する rg_sz:\<パッケージのわかりやすい名前 ><br /><br /> サービス = 対応する rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(既定値) = 対応する rg_sz: #\<ローカライズされた名前のリソース ID ><br /><br /> パッケージ = 対応する rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (ことに注意してください、キー名`SourceCodeControl`、によって既に使用されて[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、選択肢として使用できません\<PackageName >.)|(既定値) = 対応する rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>ソース管理パッケージを選択します。  
 複数ソース コントロールのプラグイン API ベースのプラグインをおよびソース管理 VSPackages を同時に登録することができます。 ソース管理プラグインまたは VSPackage を選択する処理する必要がありますいることを確認[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プラグインをロードまたは適切なタイミングで VSPackage し、必要になるまで、不要なコンポーネントの読み込みを遅らせることができます。 さらに、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の他の非アクティブな vspackages にある、メニュー項目、ダイアログ ボックス、ツールバーを含むすべての UI を削除してアクティブな VSPackage の UI を表示する必要があります。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]次の操作のいずれかが実行されるときに、ソース管理 VSPackage をロードします。  
  
-   (ソリューションがソース管理下にある場合)、ソリューションが開きます。  
  
     ソリューションまたはプロジェクトをソース管理を開いたときに、IDE は、VSPackage を読み込むには、そのソリューションの指定されたソース管理をさせます。  
  
-   ソース管理 VSPackage のメニュー コマンドのいずれかが実行されます。  
  
 VSPackage でのみは実際にされるときに必要なすべてのコンポーネントを読み込む必要がありますソース コントロールは、(それ以外の場合の遅延読み込みと呼ばれます) を使用します。  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>ソリューションに基づく VSPackage を自動スワップ  
 ソース管理 VSPackages を手動で切り替えることができますを通じて、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **オプション**ダイアログ ボックスで 、**ソース管理**カテゴリ。 ソリューションに基づくパッケージの自動スワップするには、そのソリューションを開いたときに特定のソリューションに対して指定されているソース管理パッケージが自動的にアクティブ に設定されることを意味します。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>すべてソース管理パッケージを実装する必要があります。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]両方の切り替えを処理するソース管理プラグイン (ソース管理プラグインの API の実装)、およびソース管理 vspackages にあります。  
  
 ソース コントロールのアダプターのパッケージを使用する任意のソース管理プラグインの API ベースに切り替えるにプラグインします。 ソース コントロール アダプターの中間のパッケージへの切り替えとするソース管理プラグインを決定するプロセスは、アクティブまたは非アクティブは、ユーザーに対して透過的に設定する必要があります。 アダプターのパッケージは、ソース管理プラグインがアクティブな場合に常にアクティブです。 単に読み込みとプラグインの DLL のアンロードを行う&2; つのソース管理プラグインを使用金額の切り替え。 適切な VSPackage を読み込む IDE との対話では、ソース管理 VSPackage に切り替え、します。  
  
 ソース管理ソリューションが開かれ、VSPackage のレジストリ キーは、ソリューション ファイル、VSPackage と呼ばれます。 ソリューションを開いたときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]レジストリ値を検索し、適切なソース管理 VSPackage を読み込みます。 すべてのソース管理 vspackages にある上記のレジストリ エントリが必要です。 ソース管理下にあるソリューションは、特定のソース管理 VSPackage に関連付けられている中としてマークされます。 ソース管理 VSPackages を実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>自動ソリューションに基づく VSPackage スワップを有効にします</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>。  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio のパッケージの選択と切り替えの UI  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理の VSPackage に UI とプラグインの選択の提供、**オプション**ダイアログ ボックスで 、**ソース管理**カテゴリ。 これにより、ユーザーが、アクティブなソース管理プラグインを選択または VSPackage できます。 ドロップダウン リストは次のとおりです。  
  
-   すべてのソース管理パッケージがインストールされています。  
  
-   ソース管理プラグインをすべてインストールされています。  
  
-   "None"オプションを無効にするソース コード管理  
  
 アクティブなソース コントロールの選択肢の UI のみが表示されます。 VSPackage 選択は、前の VSPackage の UI を非表示にされ、新しい UI を示しています。 アクティブな vs パッケージはユーザーごとに選択されます。 複数のコピーを持つユーザー[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]同時に開き、別のアクティブな vs パッケージ&1; つずつ使用できます。 各ユーザーが別個のインスタンスが複数のユーザーが同じコンピューターにログオンして場合、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]開く場合に、それぞれ別のアクティブな VSPackage にします。 ときに複数のインスタンスの[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース管理、最後の開いているソリューションが既定のソース管理を再起動するときにアクティブに設定する VSPackage にアクティブだった VSPackage のユーザーが閉じています。  
  
 以前のバージョンとは異なり[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、IDE の再起動は、ソース管理 VSPackages に切り替える唯一の方法ではありません。 VSPackage の選択は自動です。 パッケージを切り替えるには、Windows ユーザーの特権 (管理者またはパワー ユーザー) が必要です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [機能](../../extensibility/internals/source-control-vspackage-features.md)   
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Vspackages にあります。](../../extensibility/internals/vspackages.md)
