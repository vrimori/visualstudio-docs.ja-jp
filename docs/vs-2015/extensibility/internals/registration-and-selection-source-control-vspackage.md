---
title: 登録と選択 (ソース管理 VSPackage) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bf98c263f3452e0383f5891116849e85140b763
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818764"
---
# <a name="registration-and-selection-source-control-vspackage"></a>登録と選択 (ソース管理 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

公開するために VSPackage を登録する必要があるソース管理、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 1 つ以上のソース管理 VSPackage が登録されている場合、ユーザーは、どの VSPackage を読み込む適切なタイミングでを選択できます。 参照してください[Vspackage](../../extensibility/internals/vspackages.md) Vspackage とそれらを登録する方法の詳細についてはします。  
  
## <a name="registering-a-source-control-package"></a>ソース管理パッケージを登録します。  
 ソース管理パッケージが登録されているように、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]環境は、サポートされる機能についてしクエリを見つけることができます。 これは、ことは、遅延読み込みスキームをその機能またはコマンドが必要ですか、明示的に要求された場合にのみのパッケージのインスタンスが作成されます。  
  
 Vspackage では、情報を配置、バージョン固有のレジストリ キー hkey_local_machine \software\microsoft\visualstudio で\\*X.Y*ここで、 *X*はメジャー バージョン番号と*Y*マイナー バージョン番号です。 この実習は、複数のバージョンのサイド バイ サイドでインストールをサポートする機能を提供します。[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ユーザー インターフェイス (UI) は、ソース管理 Vspackage と複数インストールされているソース管理プラグイン (ソース管理アダプター パッケージ) を使用しての中から選択をサポートしています。 ありますのみ 1 つのアクティブなソース管理プラグインまたは VSPackage を時にします。 ただし、以下のように、IDE では、自動ソリューションに基づくパッケージ スワッピング メカニズムをソース管理プラグインと Vspackage の切り替え。 この選択方法を有効にするソース管理 VSPackage の方は、いくつか要件があります。  
  
### <a name="registry-entries"></a>レジストリ エントリ  
 ソース管理のパッケージには、次の 3 つのプライベート Guid が必要があります。  
  
- パッケージ GUID: これは、メイン ソース コントロールの実装 (このセクションでは ID_Package と呼ばれます) を含むパッケージの GUID です。  
  
- ソース コントロールの GUID。 これにソース管理 VSPackage の使用、Visual Studio のソース コントロールのスタブを登録する guid し、コマンド UI コンテキスト GUID としても使用されます。 ソース管理サービスの GUID は GUID のソース管理下で登録されています。 例では、ソース コントロールの GUID は ID_SccProvider と呼ばれます。  
  
- ソース コントロール サービス GUID: これは、プライベート サービス (このセクションでは SID_SccPkgService と呼ばれます)、Visual Studio で使用される GUID。 さらに、ソース管理パッケージは、Vspackage、ツール ウィンドウの他の Guid を定義する必要があります。  
  
  次のレジストリ エントリは、ソース管理 VSPackage によって行う必要があります。  
  
|キー名|エントリ|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(既定値) = 対応する rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(既定値) = 対応する rg_sz:\<パッケージのフレンドリ名 ><br /><br /> サービス = 対応する rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(既定値) = 対応する rg_sz: #\<ローカライズされた名前のリソース ID ><br /><br /> パッケージ = 対応する rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (なおキー名、`SourceCodeControl`で既に使用されて[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を選択肢としてご利用いただけませんと\<PackageName >.)|(既定値) = 対応する rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>ソース管理パッケージを選択します。  
 複数ソース管理プラグイン API ベースのプラグインをおよびソース管理 Vspackage を同時に登録することがあります。 ソース管理プラグインまたは VSPackage を選択するプロセスを確認する必要がありますを[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]プラグインをロードまたは適切な時に、VSPackage と必要になるまで、不要なコンポーネントの読み込みを遅らせることができます。 さらに、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]メニュー項目、ダイアログ ボックス、ツールバーなどの他の非アクティブの Vspackage からすべての UI を削除してアクティブな VSPackage の UI を表示する必要があります。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 次の操作のいずれかが実行されると、ソース管理 VSPackage を読み込みます。  
  
- ソリューションには、(ソリューションがソース管理下にある場合) が開かれます。  
  
   ソリューションまたはソース管理下にあるプロジェクトが開かれる場合、IDE には、ソース管理 VSPackage を読み込むには、そのソリューションの指定されたが行われます。  
  
- ソース管理 VSPackage のメニュー コマンドのいずれかが実行されます。  
  
  ソース管理 VSPackage にするのには実際の場合にのみ必要なすべてのコンポーネントを読み込む必要があります (それ以外の場合の遅延読み込みと呼ばれます) を使用します。  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>自動ソリューション ベースの VSPackage のスワップ  
 ソース管理 Vspackage を手動で切り替えることができますを通じて、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **オプション** ダイアログ ボックス、**ソース管理**カテゴリ。 ソリューションに基づいたパッケージの自動スワップには、そのソリューションを開いたときに特定のソリューションに対して指定されているソース管理パッケージが自動的にアクティブに設定されることを意味します。 すべてのソース管理パッケージを実装する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>します。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 両方の切り替えを処理するソース管理プラグイン (ソース管理プラグイン API を実装する)、およびソース管理 Vspackage です。  
  
 ソース コントロール アダプター パッケージを使用する任意のソース管理プラグイン API ベースに切り替えるにプラグインします。 ソース コントロール アダプターの中間パッケージへの切り替えのソース管理プラグインを決定するプロセスは、アクティブまたは非アクティブは、ユーザーに対して透過的に設定する必要があります。 アダプター パッケージは、ソース管理プラグインのアクティブなときに常にアクティブです。 単に読み込みとプラグインの DLL のアンロードを行う 2 つのソース管理プラグイン金額との間の切り替え。 適切な VSPackage を読み込む IDE との対話では、ソース管理 VSPackage に切り替え、します。  
  
 ソース管理 VSPackage は、任意のソリューションが開かれ、VSPackage のレジストリ キーが、ソリューション ファイルが呼び出されます。 ソリューションが開かれると、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]レジストリ値を検索し、適切なソース管理 VSPackage を読み込みます。 すべてのソース管理 Vspackage には、上記のレジストリ エントリが必要です。 ソース管理下にあるソリューションは、特定のソース管理 VSPackage に関連付けられたとマークされます。 ソース管理 Vspackage を実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>自動ソリューションに基づく VSPackage スワップを有効にします。  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio パッケージの選択と切り替え用の UI  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ソース管理 VSPackage の UI とプラグインの選択の提供、**オプション** ダイアログ ボックス、**ソース管理**カテゴリ。 VSPackage、ユーザーは、アクティブなソース管理プラグインを選択することができます。 ドロップダウン リストは次のとおりです。  
  
- すべてのソース管理パッケージがインストールされています。  
  
- ソース管理プラグインをすべてインストールされています。  
  
- [なし] オプション、ソース コード管理を無効にします  
  
  アクティブなソース コントロールの選択肢の UI のみが、表示されます。 VSPackage の選択は、前の VSPackage の UI を非表示にし、新しい UI を示しています。 アクティブな VSPackage は、ユーザーごとに選択されます。 複数のコピーを持つユーザー[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]同時に開き、別のアクティブな VSPackage を使用してそれぞれ、可能性のあることができます。 個別のインスタンスのことができる場合は、複数のユーザーが同じコンピューターにログオンして、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]それぞれ別のアクティブな VSPackage が開きます。 ときに複数のインスタンスの[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ユーザー、ソース管理 VSPackage、最後の開いているソリューションが既定のソース管理 VSPackage、再起動時にアクティブに設定するためにアクティブだったで閉じられています。  
  
  以前のバージョンのとは異なり[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]の IDE の再起動は、ソース管理 Vspackage を切り替えるには、唯一の方法ではありません。 VSPackage の選択は自動です。 パッケージを切り替えるには、Windows ユーザーの特権 (管理者またはパワー ユーザーではない) 必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [機能](../../extensibility/internals/source-control-vspackage-features.md)   
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackage](../../extensibility/internals/vspackages.md)

