---
title: "項目を追加、新しい項目の追加] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "追加の項目の追加、新しい項目の追加] ダイアログ ボックス"
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 項目を追加、新しい項目の追加] ダイアログ ボックス
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

項目を追加するプロセス、 **新しい項目の追加** \] ダイアログ ボックスは、レジストリ キーを使用して開始します。 次のレジストリ エントリに示すように、AddItemTemplates セクションで説明で使用可能にする項目のディレクトリの名前とパスの **新しい項目の追加** \] ダイアログ ボックスが配置されます。  
  
> [!NOTE]
>  すぐに次のコード セグメント テーブルには、レジストリ エントリに関する追加情報が含まれています。  
  
 このセクションでは、\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0Exp\\Projects\] の下にあります。  
  
 最初の GUID は、この種類のプロジェクトの CLSID2 番目の GUID では、アイテムの追加テンプレートの登録済みのプロジェクトの種類を示します。  
  
 \\{C061DB26\-5833\-11D2\-96F5\-000000000000}\\AddItemTemplates\\TemplateDirs\\ {ACEF4EB2\-57CF\-11D2\-96F4\-000000000000} \\1  
  
 @\="\#6"  
  
 "TemplatesDir「\=」\< Visual Studio SDK インストール path\\\\VSIntegration\\\\SomeFolder\\\\SomePackage\\\\SomeProject\\\\SomeProjectItems"  
  
 "SortPriority"dword:00000064 \=  
  
|名前|型|\(ファイルからデータを .rgs\)|説明|  
|--------|-------|-------------------------|--------|  
|@ \(既定値\)|REG\_SZ|\#%D IDS\_ADDITEM\_TEMPLATES\_ENTRY %|リソース ID を **項目の追加** テンプレートです。|  
|Val TemplatesDir|REG\_SZ|%TEMPLATE\_PATH%\\SomeProjectItems|ダイアログ ボックスに表示されるプロジェクト項目のパス、 **新しい項目の追加** ウィザード。|  
|Val SortPriority|REG\_DWORD|100 \([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]\)|ツリー ノードに表示されるファイルの並べ替え順序を決定、 **新しい項目の追加** \] ダイアログ ボックス。|  
  
> [!NOTE]
>  Visual c\# および Visual Basic プロジェクトの種類の GUID は次のように、:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0\-301F\-11D3\-BF4B\-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F}  
  
 ディレクトリにある % TEMPLATE\_PATH%\\SomeProjectItems TemplateDirs はの左側にあるノードが表示されている、 **新しい項目の追加** \] ダイアログ ボックスのツリーです。 ツリー内の他の要素は、そのルート ディレクトリ内のサブディレクトリに基づいています。 ファイルをプロジェクトに追加できるようには項目の右側のウィンドウで、 **新しい項目の追加** \] ダイアログ ボックス。  
  
 通常、このフォルダーは、テンプレート HTML または .cpp ファイルなど、プロジェクトのテンプレート ファイルとウィザードを起動する .vsz ファイルに格納されます。 項目を表示する方法を制御するには、ディレクトリ名とアイコンのローカライズ用 .vsdir ファイルも含めることができます。 ローカライズされた文字列は、このノード ツリーで、\[新しい項目の追加\] ダイアログを表す\] ダイアログ ボックスに表示されるキャプションです。  
  
 ただし、すべて 1 つの .vsdir ファイルに含まれている必要はありません。 ディレクトリ内のすべての項目の 1 つの .vsdir ファイルがあることができます。 詳細については、次のトピックを参照してください。[ウィザード \(します。Vsz\) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md) および[テンプレートのディレクトリの説明 \(します。Vsdir\) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  テンプレートのディレクトリに .vsdir ファイルは省略できます。 ディレクトリに、プロジェクトの要素を配置し、表示したい場合、 **新しい項目の追加** ダイアログ ボックスで、TemplatesDir ステートメントで指定したテンプレート ディレクトリにそのファイルを配置することができます。 ファイルはの右側のペインに表示されます、 **新しい項目の追加** そのプロジェクトのダイアログ ボックス。 ただし、ファイルまたはアイコンのローカライズされたキャプションを表示する場合は、テンプレート ディレクトリに .vsdir ファイルを 1 つ以上を含める必要があります。  
  
## プロジェクト項目のグループ化  
 内のフォルダーにテンプレートのグループが含まれる場合、 **新しい項目の追加** \] ダイアログ ボックスのツリーで、項目を含むルート テンプレート ディレクトリのサブディレクトリにする必要があります。 ときに、 **新しい項目の追加** \] ダイアログ ボックスがユーザーに表示されるはまた、サブフォルダーを参照してくださいし、プロジェクトの要素を選択できます。  
  
 並べ替えの優先順位のコード例では、このテンプレートのディレクトリを作成して、ツリー ノードの他の要素を基準としたツリーの場所を決定します。**新しい項目の追加** ダイアログ ボックスで、並べ替えの優先順位がすべて\] ダイアログ ボックスで、正しい位置に、項目が表示されるようにする必要があります。  
  
 実装することも、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> インターフェイスに表示される内容をフィルター処理する、 **新しい項目の追加** \] ダイアログ ボックス。 このインターフェイスを実装すると、ことができますを設定する 1 つのテンプレートのディレクトリを含む、たとえば、ディスク上のテンプレートとウィザードの 50 のファイル。 この方法により、異なる種類のプロジェクトで 20 個のファイルが 1 つのプロジェクトの種類、別の種類のプロジェクトに属している他の 30 個のファイルと一般的な種類のプロジェクトで使用可能なすべてのファイルに属していることができます。 テンプレートを作成するプロジェクトによって、この方法では、異なるテンプレート ファイルのセットを表示できます。  
  
 たとえば、Visual Basic プロジェクトで、Web プロジェクトとクライアント プロジェクトがあります。 Web フォームは、クライアント プロジェクトに追加する便利な項目あり、windows フォームは、Web サーバー プロジェクトに追加する便利な項目ではありません。 したがって、両方の種類のプロジェクトのすべてのファイルを含む 1 つのテンプレートのディレクトリを作成できます。 実装することによって、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, 、プロジェクトまたはプロジェクトでプロジェクトの設定の種類に基づく表示されない項目を非表示にすることができます。  
  
## プロジェクト項目のフィルター処理  
 `IVsFilterAddProjectItemDlg2` ツリー \(左側のウィンドウ\) とプロジェクト ファイル \(右ペイン\) 内の要素の次の方法でフィルター処理を提供します。  
  
-   ローカライズされた名前 \(.vsdir ファイルに含まれているダイアログ ボックスに表示されるキャプション\) によって提供される `IVsFilterAddProjectItemDlg`します。  
  
-   ファイルとディスク上のフォルダーの実際の名前 \(ローカライズされていない — .vsdir ファイルがありません\) によって提供される `IVsFilterAddProjectItemDlg`します。  
  
-   カテゴリ別にによって提供される `IVsFilterAddProjectItemDlg2`します。  
  
 カテゴリによるフィルター処理するには、「Web フォーム」など、.vsdir ファイル内のアイテムまたは Visual Basic では"クライアント item"カテゴリ文字列を指定します。 ダイアログ ボックスのコードに、.vsdir ファイルをカテゴリ分類を取得しに渡します。 実装にその情報を渡すことができますし、 `IVsFilterAddProjectItemDlg2` をフィルター処理する、 **新しい項目の追加** ダイアログ ボックスのカテゴリを表示します。 Win32 アプリケーションによって、クライアントまたは Web ページの項目をフィルターすることもできます。 また、どの [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] Microsoft Foundation Classes \(MFC\)、またはアクティブ テンプレート ライブラリ \(ATL\) の項目として項目をタグ付けします。 これらの項目を識別する場合、プロジェクト システムは、システムにカテゴリと分類に基づいてフィルターを処理できるように、独自の分類を定義できます。  
  
 このフィルターの機能を実装する場合は、非表示にするすべての項目のテーブルにマップする必要はありません。 単に項目の種類に分類し、.vsdir ファイルまたはファイルに分類できます。 いずれかのインターフェイスを実装することによって特定の分類がある項目が非表示できます。 これにより、内の項目を行うことができます、 **新しい項目の追加** プロジェクト内の状態に基づいて、ダイアログ ボックスの動的です。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [プロジェクトおよび項目テンプレートを登録します。](../../extensibility/internals/registering-project-and-item-templates.md)   
 [通常、プロジェクトの拡張に使用されるオブジェクトの Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [テンプレートのディレクトリの説明 \(します。Vsdir\) ファイル](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [ウィザード \(します。Vsz\) ファイル](../../extensibility/internals/wizard-dot-vsz-file.md)