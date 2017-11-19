---
title: "VSTO アドインのレジストリ エントリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
ms.assetid: 319e5bbc-0234-4af0-91ce-54bcfafc173f
caps.latest.revision: "79"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32fd9fe36f029296d52127cf1f3be9e3c205d82b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO アドインのレジストリ エントリ
  Visual Studio で作成した VSTO アドインを配置するときには、一連のレジストリ エントリを作成する必要があります。 それらのレジストリ エントリで指定する情報によって、Microsoft Office アプリケーションは VSTO アドインを検出し、読み込むことができます。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 プロジェクトをビルドすると、Visual Studio によって開発用コンピューター上にレジストリ エントリが作成されるので、VSTO アドインを簡単に実行およびデバッグできます。 ClickOnce を使用して VSTO アドインを配置する場合は、エンド ユーザーのコンピューター上にレジストリ エントリが自動的に作成されます。 Windows インストーラーを使用して VSTO アドインを配置する場合は、InstallShield Limited Edition プロジェクトを構成して、エンド ユーザーのコンピューター上にレジストリ エントリを作成する必要があります。  
  
 VSTO アドインの読み込みプロセス中にレジストリ エントリがどのように使用されるかについては、「 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)」を参照してください。  
  
> [!NOTE]  
>  このトピックでは、テキスト *アドイン ID* は VSTO アドインの一意の ID を表します。 既定では、この ID は VSTO アドイン アセンブリの名前です。  
  
## <a name="registering-vsto-add-ins-for-the-current-user-vs-all-users"></a>現在のユーザーとすべてのユーザー用の VSTO アドインの登録すべてのユーザー  
 VSTO アドインをインストールするときは、次の 2 つの方法で登録できます。  
  
-   現在のユーザーのみ (VSTO アドインのインストール時にコンピューターにログオンしていたユーザーのみが使用可能)。 この場合、レジストリ エントリは HKEY_CURRENT_USER の下に作成されます。  
  
-   すべてのユーザー (コンピューターにログオンしたすべてのユーザーが VSTO アドインを使用可能)。 この場合、レジストリ エントリは HKEY_LOCAL_MACHINE の下に作成されます。  
  
 Visual Studio を使用して作成したすべての VSTO アドインは、現在のユーザー用に登録できます。 ただし、特定のシナリオに限り、VSTO アドインをすべてのユーザー用に登録できます。 これらのシナリオは、コンピューター上の Microsoft Office のバージョン、および VSTO アドインの配置方法によって異なります。  
  
### <a name="microsoft-office-version"></a>Microsoft Office のバージョン  
 Office アプリケーションは、HKEY_LOCAL_MACHINE または HKEY_CURRENT_USER に登録されている VSTO アドインを読み込むことができます。  
  
 HKEY_LOCAL_MACHINE に登録された VSTO アドインを読み込むには、コンピューターに更新パッケージ 976477 がインストールされている必要があります。 詳細については、 [http://go.microsoft.com/fwlink/?LinkId=184923](http://go.microsoft.com/fwlink/?LinkId=184923)を参照してください。  
  
### <a name="deployment-type"></a>配置タイプ  
 ClickOnce を使用して VSTO アドインを配置する場合は、現在のユーザー用にのみ VSTO アドインを登録できます。 これは、ClickOnce が HKEY_CURRENT_USER の下へのキーの作成のみをサポートしているためです。 VSTO アドインをコンピューター上のすべてのユーザー用に登録する場合は、Windows インストーラーを使用して VSTO アドインを配置する必要があります。 これらの展開の種類の詳細については、次を参照してください。 [ClickOnce を使用して Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)と[Windows インストーラーを使用した Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-windows-installer.md)です。  
  
## <a name="registry-entries"></a>レジストリ エントリ  
 必要な VSTO アドイン レジストリ エントリは、Visio を除くすべてのアプリケーションで次のレジストリ キーの下にあります。 *Root* は HKEY_CURRENT_USER または HKEY_LOCAL_MACHINE です。  
  
 **Visio を除くすべてのアプリケーション**  
  
|Office のバージョン|構成パス|  
|--------------------|------------------------|  
|32 ビット|*ルート*\Software\Microsoft\Office\\*アプリケーション名*\Addins\\*アドイン ID*|  
|64 ビット|*ルート*\Software\Wow6432Node\Microsoft\Office\\*アプリケーション名*\Addins\\*アドイン ID*|  
  
 **Visio**  
  
|Office のバージョン|構成パス|  
|--------------------|------------------------|  
|32 ビット|*ルート*\Software\Microsoft\Visio\Addins\\*アドイン ID*|  
|64 ビット|*ルート*\Software\Wow6432Node\Visio\Addins\\*アドイン ID*|  
  
 このレジストリ キーの下にあるエントリを次の表に示します。  
  
|入力|型|値|  
|-----------|----------|-----------|  
|**説明**|REG_SZ|必須です。 VSTO アドインの簡単な説明。<br /><br /> この説明は、ユーザーが Microsoft Office アプリケーションの **[オプション]** ダイアログ ボックスの **[アドイン]** ペインで VSTO アドインを選択したときに表示されます。|  
|**FriendlyName**|REG_SZ|必須です。 Microsoft Office アプリケーションの **[COM アドイン]** ダイアログ ボックスに表示される、VSTO アドインの説明的な名前。 既定値は VSTO アドイン ID です。|  
|**LoadBehavior**|REG_DWORD|必須です。 アプリケーションが VSTO アドインを読み込みを試行した時点と、VSTO アドインの現在の状態 (読み込まれているかアンロードされているか) を示す値。<br /><br /> このエントリの既定値は 3 です。これは、VSTO アドインが起動時に読み込まれたことを示します。 詳細については、「 [LoadBehavior の値](#LoadBehavior)」を参照してください。 **注:** VSTO アドインでユーザーを無効に、その操作によって**LoadBehavior** HKEY_CURRENT_USER レジストリ ハイブの値。 各ユーザーに対して、HKEY_CURRENT_USER ハイブの **LoadBehavior** の値によって、HKEY_LOCAL_MACHINE ハイブで定義された既定の **LoadBehavior** が上書きされます。|  
|**Manifest**|REG_SZ|必須です。 VSTO アドインの配置マニフェストの完全なパス。 ローカル コンピューター上の場所、ネットワーク共有 (UNC)、Web サーバー (HTTP) のいずれかを指定できます。<br /><br /> Windows インストーラーを使用してソリューションを配置する場合、 **マニフェスト** パスにプレフィックス " **file:///** " を追加する必要があります。 文字列を追加することも必要があります**(& a) #124; vstolocal** (つまり、パイプ文字**&#124;**続く**vstolocal**) このパスの末尾にします。 これにより、ClickOnce キャッシュではなく、インストール フォルダーからソリューションが読み込まれます。 詳細については、「 [Deploying an Office Solution by Using Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)」を参照してください。 **注:**開発用コンピューターで VSTO アドインをビルドすると、Visual Studio は自動的に追加、 **(& a) #124; vstolocal**このレジストリ エントリへの文字列。|  
  
###  <a name="OutlookEntries"></a> Outlook フォーム領域のレジストリ エントリ  
 Outlook 用 VSTO アドインにカスタム フォーム領域を作成する場合は、フォーム領域を Outlook に登録するために追加のレジストリ エントリが使用されます。 これらのエントリは、フォーム領域がサポートするメッセージ クラスごとに異なるレジストリ キーの下に作成されます。 これらのレジストリ キーは次の場所にあります。 *Root* は HKEY_CURRENT_USER または HKEY_LOCAL_MACHINE です。  
  
 *ルート*\Software\Microsoft\Office\Outlook\FormRegions\\*message クラス*  
  
 すべての VSTO アドインで共有されるその他のレジストリ エントリと同様に、プロジェクトをビルドすると、Visual Studio によって開発用コンピューター上にフォーム領域レジストリ エントリが作成されます。 ClickOnce を使用して VSTO アドインを配置する場合は、エンド ユーザーのコンピューター上にレジストリ エントリが自動的に作成されます。 Windows インストーラーを使用して VSTO アドインを配置する場合は、InstallShield Limited Edition プロジェクトを構成して、エンド ユーザーのコンピューター上にレジストリ エントリを作成する必要があります。  
  
 フォーム領域レジストリ エントリの詳細については、次を参照してください。[カスタム フォームのフォーム領域の場所の指定](http://msdn.microsoft.com/library/office/ff868998.aspx)です。 Outlook フォーム領域の詳細については、「 [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md)」を参照してください。  
  
##  <a name="LoadBehavior"></a> LoadBehavior の値  
 **LoadBehavior**の下のエントリ、*ルート*\Software\Microsoft\Office\\*アプリケーション名*\Addins\\*アドインID*キーには、VSTO アドインでの実行時の動作を指定する値のビットごとの組み合わせが含まれています。 最下位のビット (値 0 および 1) は、VSTO アドインが現在アンロードされているか、または読み込み済みであるかを示します。 その他のビットは、アプリケーションが VSTO アドインを読み込もうとしていることを示します。  
  
 通常、VSTO アドインがエンド ユーザーのコンピューターにインストールされている場合は、 **LoadBehavior** エントリは 10 進数の 0、3、または 16 に設定されます。 既定では、VSTO アドインをビルドまたは発行すると、Visual Studio によってアドインの **LoadBehavior** エントリが 3 に設定されます。  
  
 **LoadBehavior** エントリに指定できるすべての値を次の表に示します。 この表では、VSTO アドインを手動またはプログラムによって読み込む場合も示されています。 VSTO アドインを手動で読み込むには、アプリケーションの **[COM アドイン]** ダイアログ ボックスで、VSTO アドインの横にあるチェック ボックスをオンにします。 VSTO アドインをプログラムによって読み込むには、VSTO アドインを表す <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> オブジェクトの <xref:Microsoft.Office.Core.COMAddIn> プロパティを **true**」を参照してください。  
  
|値 (10 進形式)|VSTO アドインの状態|VSTO アドインの読み込み動作|説明|  
|--------------------------|-------------------------|--------------------------------|-----------------|  
|0|アンロードされました|自動的に読み込まない|VSTO アプリケーションは自動的にアドインを読み込みません。 VSTO アドインを読み込むには、ユーザーが手動で読み込むか、またはプログラムによって読み込みます。<br /><br /> VSTO アドインの読み込みが成功した場合、 **LoadBehavior** の値は 0 のままですが、 **[COM アドイン]** ダイアログ ボックスの VSTO アドインの状態は更新されて、VSTO アドインが読み込み済みであることが示されます。|  
|1|読み込み|自動的に読み込まない|VSTO アプリケーションは自動的にアドインを読み込みません。 VSTO アドインを読み込むには、ユーザーが手動で読み込むか、またはプログラムによって読み込みます。<br /><br /> アプリケーションの起動後、 **[COM アドイン]** ダイアログ ボックスには VSTO アドインが読み込み済みであることが示されますが、手動またはプログラムによって読み込まれるまで VSTO アドインは実際には読み込まれません。<br /><br /> VSTO アドインの読み込みが成功した場合、 **LoadBehavior** の値は 0 に変更されます。アプリケーションの終了後も 0 のままです。|  
|2|アンロードされました|スタート時に読み込む|アプリケーションは自動的に VSTO アドインを読み込みません。 VSTO アドインを読み込むには、ユーザーが手動で読み込むか、またはプログラムによって読み込みます。<br /><br /> VSTO アドインの読み込みが成功した場合、 **LoadBehavior** の値は 3 に変更されます。アプリケーションの終了後も 3 のままです。|  
|3|読み込み|スタート時に読み込む|アプリケーションが起動時に VSTO アドインを読み込もうとします。 これは、Visual Studio で VSTO アドインをビルドまたは発行した場合の既定値です。<br /><br /> VSTO アドインの読み込みが成功した場合、 **LoadBehavior** の値は 3 のままです。 VSTO アドインの読み込み中にエラーが発生した場合、 **LoadBehavior** の値は 2 に変更されます。アプリケーションの終了後も 2 のままです。|  
|9|アンロードされました|必要に応じて読み込む|アプリケーションは自動的に VSTO アドインを読み込みません。 VSTO アドインを読み込むには、ユーザーが手動で読み込むか、またはプログラムによって読み込みます。<br /><br /> VSTO アドインの読み込みが成功した場合、 **LoadBehavior** の値は 9 に変更されます。|  
|9|読み込み|必要に応じて読み込む|VSTO アドインの機能を使用する UI 要素 (たとえば、リボンのカスタム ボタン) をユーザーがクリックしたときなど、アプリケーションで要求されたときにのみ VSTO アドインが読み込まれます。<br /><br /> VSTO アドインの読み込みが成功した場合、 **LoadBehavior** の値は 9 のままですが、 **[COM アドイン]** ダイアログ ボックスの VSTO アドインの状態は更新されて、VSTO アドインが現在読み込み済みであることが示されます。 VSTO アドインの読み込み中にエラーが発生した場合は、 **LoadBehavior** の値が 8 に変更されます。|  
|16|読み込み|初回に読み込み、その後必要に応じて読み込む|VSTO アドインを必要に応じて読み込む場合は、この値を設定します。 ユーザーが最初にアプリケーションを起動したときに、アプリケーションが VSTO アドインを読み込みます。 ユーザーが次にアプリケーションを実行したときには、VSTO アドインによって定義された UI 要素が読み込まれますが、VSTO アドインはユーザーが VSTO アドインに関連付けられた UI 要素をクリックするまで読み込まれません。<br /><br /> VSTO アドインの最初の読み込みが成功した場合、VSTO アドインが読み込まれている間 **LoadBehavior** の値は 16 のままです。 アプリケーションの終了後、 **LoadBehavior** の値は 9 に変更されます。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での Office ソリューションのアーキテクチャ](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [Office ソリューションのビルド](../vsto/building-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  