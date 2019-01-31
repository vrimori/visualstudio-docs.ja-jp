---
title: 'チュートリアル: 手動で再署名が要求されるされないブランド情報を保持する ClickOnce アプリケーションの展開 |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eef3d0732921bdd22b5753db6d7f769371bc335a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021599"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>チュートリアル: 手動で再署名が不要な ClickOnce アプリケーションをデプロイして、商標を保持
作成するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションと、それを発行する顧客に渡すを展開し、顧客は、配置マニフェストを更新して再署名に従来しました。 ほとんどの場合に推奨される方法ですが、.NET Framework 3.5 を使用すると、作成[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]新しい配置マニフェストを再生成することがなく、顧客によって展開できる展開します。 詳細については、次を参照してください。[再署名なしのテストと実稼働サーバーの展開の ClickOnce アプリケーション](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)します。  
  
 作成するときに、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーションと、それを発行する顧客に渡すと展開、アプリケーション、お客様のブランド化を使用できますまたはブランド化を維持することができます。 たとえば、アプリケーションが独自のアプリケーションを 1 つである場合は、ブランド化を保持するためにする可能性があります。 場合は、アプリケーションは、顧客ごとにカスタマイズされた高、お客様のブランド化を使用する場合があります。 .NET Framework 3.5 では、展開するには、組織にアプリケーションに付与するとするブランド化を保持するために、パブリッシャー情報、およびセキュリティの署名を使用できます。 詳細については、次を参照してください。[作成の ClickOnce アプリケーションをデプロイする他のユーザーの](../deployment/creating-clickonce-applications-for-others-to-deploy.md)します。  
  
> [!NOTE]
>  このチュートリアルでデプロイ手動で作成するかを使用して、コマンド ライン ツール*Mage.exe*またはグラフィカルなツールで*MageUI.exe*します。 手動でデプロイの詳細については、次を参照してください。[チュートリアル。ClickOnce アプリケーションを手動で展開](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルの手順を実行するには、次のものが必要。  
  
-   Windows フォーム アプリケーションをデプロイする準備が完了したらです。 このアプリケーションが参照されますとして*WindowsFormsApp1*します。  
  
-   Visual Studio または Windows SDK。  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>複数の展開とブランド化のサポートが Mage.exe を使用して ClickOnce アプリケーションをデプロイするには  
  
1. Visual Studio コマンド プロンプトを開き、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]コマンド プロンプト、および格納するディレクトリに変更、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ファイル。  
  
2. 配置の現在のバージョンにちなんだ名前のディレクトリを作成します。 初めてアプリケーションを展開する場合は、おそらくを選択します**1.0.0.0**します。  
  
   > [!NOTE]
   >  配置のバージョンは、アプリケーション ファイルのバージョンとは異なる可能性があります。  
  
3. という名前のサブディレクトリを作成する**bin**し、実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、すべてのアプリケーション ファイルをコピーします。  
  
4. Mage.exe への呼び出しを使用してアプリケーション マニフェストを生成します。  
  
   ```cmd  
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
   ```  
  
5. デジタル証明書をアプリケーション マニフェストに署名します。  
  
   ```cmd  
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
   ```  
  
6. 呼び出しで配置マニフェストを生成*Mage.exe*します。 既定では、 *Mage.exe*マークは、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]その it を両方オンラインで実行できるように、オフライン インストールされているアプリケーションとして展開します。 アプリケーションで使用できるように、ユーザーがオンラインの場合にのみ使用して、`-i`引数の値を持つ`f`します。 このアプリケーションは、複数のデプロイ機能を活用するための除外、`-providerUrl`引数*Mage.exe*します。 (を除くより前のバージョン 3.5 では、.NET Framework のバージョンで`-providerUrl`のオフライン アプリケーションがエラーになります)。  
  
   ```cmd  
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
   ```  
  
7. 配置マニフェストに署名しません。  
  
8. すべてのファイルをネットワーク上のアプリケーションをデプロイすると、顧客に提供します。  
  
9. この時点では、顧客は彼自身の自動生成された証明書で配置マニフェストに署名する必要があります。 たとえば、Adventure Works という会社の顧客が動作する場合を生成できますを使用して、自己署名証明書、 *MakeCert.exe*ツール。 次に、使用、 *Pvk2pfx.exe*ツールによって作成されたファイルを結合する*MakeCert.exe*に渡すことが PFX ファイルに*Mage.exe*します。  
  
    ```cmd  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. 次に、顧客は、配置マニフェストに署名するのにこの証明書を使用します。  
  
    ```cmd  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. お客様は、ユーザーにアプリケーションをデプロイします。  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>複数の展開とブランド化のサポートが MageUI.exe を使用して ClickOnce アプリケーションをデプロイするには  
  
1. Visual Studio コマンド プロンプトを開き、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]コマンド プロンプト、および格納するディレクトリに移動し、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ファイル。  
  
2. という名前のサブディレクトリを作成する**bin**し、実行可能ファイル、アセンブリ、リソース、およびデータ ファイルを含む、すべてのアプリケーション ファイルをコピーします。  
  
3. 配置の現在のバージョンにちなんだ名前のサブディレクトリを作成します。 初めてアプリケーションを展開する場合は、おそらくを選択します**1.0.0.0**します。  
  
   > [!NOTE]
   >  配置のバージョンは、アプリケーション ファイルのバージョンとは異なる可能性があります。  
  
4. 移動、 \\ **bin**手順 2. で作成したディレクトリにディレクトリ。  
  
5. グラフィカル ツールを起動*MageUI.exe*します。  
  
   ```cmd  
   MageUI.exe  
   ```  
  
6. 選択して新しいアプリケーション マニフェストを作成する**ファイル**、**新規**、 **Application Manifest**  メニューから。  
  
7. 既定の**名前** タブで、このデプロイの名前とバージョン番号を入力します。 値を指定することも、**パブリッシャー**、どちらを使用するアプリケーションのショートカット リンク、[スタート] メニューのフォルダー名として配置されるとき。  
  
8. 選択、**アプリケーション オプション** タブでをクリックし、**信頼情報用のアプリケーション マニフェストを使用して**します。 これにより、このブランドのサードパーティ製[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]アプリケーション。  
  
9. 選択、**ファイル** タブでをクリックし、**参照**横に、**アプリケーション ディレクトリ**テキスト ボックス。  
  
10. 手順 2. で作成したアプリケーション ファイルを含むディレクトリを選択し、をクリックして**OK**フォルダーの選択 ダイアログ ボックスにします。  
  
11. をクリックして、 **Populate**ファイルの一覧にすべてのアプリケーション ファイルを追加するボタンをクリックします。 アプリケーションには、複数の実行可能ファイルが含まれている場合は、スタートアップ アプリケーションとしては、この展開のメイン実行可能ファイルをマークをオンに**エントリ ポイント**から、**ファイルの種類**ドロップダウン リスト。 (アプリケーションには、1 つの実行可能ファイルのみが含まれる場合*MageUI.exe*を対象として設定されます)。  
  
12. 選択、**必要なアクセス許可**タブし、アプリケーションをアサートする必要がある信頼のレベルを選択します。 既定値は**完全信頼**、ほとんどのアプリケーションに適したされます。  
  
13. 選択**ファイル**、**保存**メニューのおよびアプリケーション マニフェストを保存します。 保存すると、アプリケーション マニフェストに署名するように促されます。  
  
14. 場合は、ファイル システム上のファイルとして格納されている証明書がある場合を使用して、**証明書ファイルと符号**し、省略記号を使用して、ファイル システムから証明書を選択します (**...**) ボタンをクリックします。  
  
     - または -  
  
     証明書がコンピューターからアクセスできる証明書ストアに保持されている場合は、選択、**格納された証明書オプションを使用してサインイン**、表示された一覧から証明書を選択します。  
  
15. 選択**ファイル**、**新規**、**配置マニフェスト**、配置マニフェストを作成するメニューから、次に、**名前** タブで、指定、名前とバージョン番号 (**1.0.0.0**この例では)。  
  
16. 切り替えて、**更新**タブをクリックし、このアプリケーションを更新する頻度を指定します。 アプリケーションで使用する場合、 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Deployment API 自体は、更新プログラムのチェックをオフにチェック ボックスをオン**アプリケーションの更新プログラムを確認する必要があります**します。  
  
17. 切り替えて、**アプリケーション参照**タブ。クリックして設定のこのタブで値をすべて事前、 **マニフェストの**前の手順で作成したボタンをクリックし、アプリケーション マニフェストを選択します。  
  
18. 選択**保存**と配置マニフェストをディスクに保存します。 保存すると、アプリケーション マニフェストに署名するように促されます。 クリックして**キャンセル**署名せずにマニフェストを保存します。  
  
19. お客様には、すべてのアプリケーション ファイルを提供します。  
  
20. この時点では、顧客は彼自身の自動生成された証明書で配置マニフェストに署名する必要があります。 たとえば、Adventure Works という会社の顧客が動作する場合を生成できますを使用して、自己署名証明書、 *MakeCert.exe*ツール。 次に、使用、 *Pvk2pfx.exe*ツールによって作成されたファイルを結合する*MakeCert.exe*に渡すことが PFX ファイルに*MageUI.exe*します。  
  
    ```cmd  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. 生成された証明書を使って、顧客ようになりましたが、配置マニフェストで配置マニフェストを開くことで*MageUI.exe*、し、これを保存します。 署名 ダイアログ ボックスが表示されたら、選択**証明書ファイルと符号**オプション、およびディスクに保存していますが、PFX ファイルを選択します。  
  
22. お客様は、ユーザーにアプリケーションをデプロイします。  
  
## <a name="see-also"></a>関連項目  
 [Mage.exe (マニフェストの生成および編集ツール)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert](/windows/desktop/SecCrypto/makecert)