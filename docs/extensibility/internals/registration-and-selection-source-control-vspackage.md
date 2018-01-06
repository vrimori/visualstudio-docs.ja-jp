---
title: "登録と選択 (ソース コントロール VSPackage) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b0f02abe4cad58db27700aee3c29ec8d2dd7a7e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="registration-and-selection-source-control-vspackage"></a>登録と選択 (ソース コントロール VSPackage)
公開するために VSPackage を登録する必要があるソース管理、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 1 つ以上のソース管理 VSPackage が登録されている場合、ユーザーはどの VSPackage を読み込むことが適切なタイミングでを選択できます。 参照してください[Vspackage](../../extensibility/internals/vspackages.md) Vspackage とこれらを登録する方法の詳細についてはします。  
  
## <a name="registering-a-source-control-package"></a>ソース管理パッケージを登録します。  
 ソース管理パッケージを登録できるように、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]環境は、サポートされる機能について、およびクエリを見つけることができます。 これは、パッケージのインスタンスを作成するの機能やコマンドが必要かが明示的に要求された場合にのみ、遅延読み込みスキームに従ってです。  
  
 Vspackage では、バージョン固有のレジストリ キー、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio の情報を格納\\*X.Y*ここで、 *X*はメジャー バージョン番号と*Y*マイナー バージョン番号です。 この実習での複数のバージョンのサイド バイ サイド インストールをサポートする機能は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ユーザー インターフェイス (UI) は、ソース管理 Vspackage と複数インストールされているソース管理プラグイン (ソース管理アダプター パッケージ) 経由での中から選択をサポートしています。 ありますのアクティブなソース管理プラグインまたは VSPackage を 1 つだけ、時にします。 ただし、以下のとおり、IDE では、自動ソリューションに基づくパッケージ交換メカニズムをソース管理プラグインと Vspackage の切り替え。 この選択方法を有効にするソース管理 VSPackage の部分は、いくつか要件があります。  
  
### <a name="registry-entries"></a>レジストリ エントリ  
 ソース管理パッケージには、次の 3 つのプライベート Guid が必要があります。  
  
-   パッケージの GUID。 これは、メインをソース コントロールの実装 (ここでは ID_Package と呼ばれます) を含むパッケージの GUID です。  
  
-   ソース コントロールの GUID。 これは、ソース管理、Visual Studio のソース コントロールのスタブを登録するために使用する VSPackage の GUID でありコマンド UI コンテキスト GUID としても使用されます。 ソース管理サービスの GUID は GUID のソース管理下にある登録します。 この例では、ソース コントロールの GUID を ID_SccProvider と呼びます。  
  
-   ソース管理サービス GUID: プライベート サービス (このセクションでは SID_SccPkgService と呼ばれます)、Visual Studio によって使用される GUID です。 さらに、ソース管理パッケージは、Vspackage、ツール ウィンドウの他の Guid を定義する必要があります。  
  
 次のレジストリ エントリは、ソース管理 VSPackage で行う必要があります。  
  
|キー名|エントリ|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(既定値) = 対応する rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(既定値) = 対応する rg_sz:\<パッケージの表示名 ><br /><br /> サービス = 対応する rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(既定値) = 対応する rg_sz: #\<ローカライズされた名前のリソース ID ><br /><br /> パッケージ = 対応する rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (ことに注意してください、キー名`SourceCodeControl`が既に使用して[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の選択肢としては使用できません、 \<PackageName >.)|(既定値) = 対応する rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>ソース管理パッケージを選択します。  
 複数ソース コントロールのプラグイン API ベースのプラグイン、およびソース管理の Vspackage を同時に登録することがあります。 ソース管理プラグインまたは VSPackage を選択した場合のプロセスで、ことを確認する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プラグインをロードまたは適切な時に、VSPackage、不要なコンポーネントの読み込みが必要になるまでに任せることができます。 さらに、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]メニュー項目、ダイアログ ボックス、ツールバーなどの他の非アクティブの Vspackage からすべての UI を削除してアクティブな VSPackage の UI を表示する必要があります。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]次の操作のいずれかが実行されるときに、ソース管理の VSPackage をロードします。  
  
-   (ソリューションでは、ソース管理下にある) 場合は、ソリューションが開かれます。  
  
     ソリューションまたはプロジェクトをソース コントロールを開いたときに、IDE は VSPackage に読み込むには、そのソリューションの指定されたソース管理をさせます。  
  
-   VSPackage のソース コントロールのメニュー コマンドのいずれかが実行されます。  
  
 VSPackage は実際にしようとするときにのみに必要なすべてのコンポーネントを読み込む必要がありますをソース コントロールには、(それ以外の場合の遅延読み込みと呼ばれます) が使用されます。  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>ソリューションに基づく自動の VSPackage のスワップ  
 ソース管理の Vspackage を手動で切り替えることができますを通じて、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **オプション**ダイアログ ボックスの 、**ソース管理**カテゴリ。 ソリューションに基づくパッケージの自動スワップするには、そのソリューションを開いたときに特定のソリューションに対して指定されているソース管理パッケージが自動的にアクティブに設定されることを意味します。 すべてのソース管理パッケージを実装する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>です。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]両方の切り替えを処理およびソース管理の Vspackage のソース管理プラグイン (ソース管理プラグイン API を実装する)。  
  
 ソース コントロール アダプター パッケージを使用する任意のソース管理プラグイン API ベースに切り替えるにプラグインします。 中間のソース管理アダプター パッケージへの切り替えとするソース管理プラグインの決定のプロセスはアクティブまたは非アクティブでは、ユーザーに対して透過的に設定する必要があります。 アダプター パッケージは、常にアクティブなすべてソース管理プラグインがアクティブなときです。 単に読み込みおよびプラグインの DLL をアンロードする 2 つのソース管理プラグイン金額を切り替えます。 交代ソース コントロール VSPackage に、ただしでは、適切な VSPackage を読み込むよう IDE に対話します。  
  
 ソース管理の任意のソリューションが開かれ、VSPackage のレジストリ キーは、ソリューション ファイルと、VSPackage が呼び出されます。 ソリューションを開いたときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]レジストリ値を検出し、適切なソース管理 VSPackage を読み込みます。 Vspackage のすべてのソース管理には、上記のレジストリ エントリが必要です。 ソース管理下にあるソリューションは、特定のソース管理 VSPackage に関連付けられている中としてマークされます。 ソース管理の Vspackage を実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>自動ソリューションに基づく VSPackage スワップを有効にします。  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio のパッケージの選択と切り替えの UI  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供する VSPackage のソース コントロールの UI でプラグインの選択、**オプション**ダイアログ ボックスの 、**ソース管理**カテゴリ。 VSPackage、ユーザーが、アクティブなソース管理プラグインを選択できます。 ドロップダウン リストは次のとおりです。  
  
-   ソース管理パッケージをすべてインストール  
  
-   ソース管理プラグインをすべてインストールされています。  
  
-   "None"オプションをソース コード管理を無効にします。  
  
 UI のアクティブなソース コントロールの選択肢のみが表示されます。 VSPackage の選択は、以前の VSPackage の UI を非表示にし、新しい 1 つの UI を示しています。 ユーザーごとに、アクティブな VSPackage が選択されます。 複数のコピーを持つユーザー[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]同時に開き、別のアクティブな VSPackage を使用することができます可能性のある 1 つずつです。 各ユーザーが別個のインスタンスを持つことができる場合、複数のユーザーが同じコンピューターにログオンして、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]開く場合に、それぞれ別のアクティブな VSPackage にします。 ときの複数のインスタンス[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ユーザーをソース コントロールがアクティブであった最後の開いているソリューションが既定のソース コントロールの再起動時にアクティブな設定を VSPackage を VSPackage で閉じられています。  
  
 以前のバージョンのとは異なり[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE の再起動は、Vspackage のソース管理をスイッチする唯一の方法ではなくなりました。 VSPackage の選択は自動です。 パッケージを切り替えるには、Windows のユーザー特権 (管理者またはパワー ユーザーではない) 必要があります。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [機能](../../extensibility/internals/source-control-vspackage-features.md)   
 [ソース管理プラグインを作成します。](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackage](../../extensibility/internals/vspackages.md)