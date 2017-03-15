---
title: "チュートリアル : 再署名が不要で商標を保持する ClickOnce アプリケーションの手動配置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "商標"
  - "ClickOnce アプリケーション, 配置 (他のユーザーによる)"
  - "ClickOnce 配置, 手動"
  - "ClickOnce 配置, SDK ツール"
  - "顧客配置"
  - "マニフェスト [ClickOnce]"
  - "ClickOnce の手動配置"
  - "複数の ClickOnce 配置と商標"
  - "保持される商標"
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# チュートリアル : 再署名が不要で商標を保持する ClickOnce アプリケーションの手動配置
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを作成し、顧客に提供して発行および配置する場合、従来は顧客が配置マニフェストを更新して再署名する必要がありました。ほとんどの場合はこの方法が適していることに変わりありませんが、.NET Framework 3.5 では、顧客が新しい配置マニフェストを再生成しなくても配置できる [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を作成できます。  詳細については、「[再署名を行わない ClickOnce アプリケーションの配置 \(テスト サーバーおよび運用サーバー\)](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)」を参照してください。  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションを作成し、顧客に提供して発行および配置する場合、アプリケーションは、顧客の商標を使用することも、作成者の商標を保持することもできます。  たとえば、アプリケーションが単一商標権を所有するアプリケーションである場合、作成者の商標を保持することができます。  アプリケーションが顧客ごとに大きくカスタマイズされる場合は、顧客の商標を使用できます。  .NET Framework 3.5 では、アプリケーションを組織に提供して配置するときに、作成者の商標、発行者情報、およびセキュリティ署名を保持することができます。  詳細については、「[開発者以外が配置する ClickOnce アプリケーションの作成](../deployment/creating-clickonce-applications-for-others-to-deploy.md)」を参照してください。  
  
> [!NOTE]
>  このチュートリアルでは、コマンド ライン ツールの Mage.exe またはグラフィカル ツールの MageUI.exe を使用して配置を手動で作成します。  手動配置の詳細については、「[チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルの手順を実行するには、次のものが必要です。  
  
-   配置できる状態にある Windows フォーム アプリケーション。  このアプリケーションを、WindowsFormsApp1 と呼びます。  
  
-   Visual Studio または Windows SDK  
  
### 複数の配置および商標をサポートする ClickOnce アプリケーションを Mage.exe を使用して配置するには  
  
1.  Visual Studio コマンド プロンプトまたは [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] のコマンド プロンプトを開き、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のファイルを格納するディレクトリに移動します。  
  
2.  ディレクトリを作成し、配置の現在のバージョンに対応させて名前を付けます。  初めてアプリケーションを配置する場合であれば、1.0.0.0 などの名前を付けます。  
  
    > [!NOTE]
    >  配置のバージョンは、アプリケーション ファイルのバージョンとは異なる場合もあります。  
  
3.  bin サブディレクトリを作成し、実行可能ファイル、アセンブリ、リソース ファイル、データ ファイルなど、すべてのアプリケーション ファイルをこのサブディレクトリにコピーします。  
  
4.  Mage.exe を呼び出して、アプリケーション マニフェストを作成します。  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  自分のデジタル証明書を使用してアプリケーション マニフェストに署名します。  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Mage.exe を呼び出して、配置マニフェストを作成します。  既定では、Mage.exe は [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置を、オンラインでもオフラインでも実行できるように、インストール アプリケーションとして指定します。  ユーザーがオンラインの場合にだけアプリケーションを使用できるようにする場合は、`-i` 引数の値に `f` を指定して使用します。  このアプリケーションは複数配置機能を利用するので、Mage.exe の引数 `-providerUrl` は除外してください。  \(Version 3.5 より前のバージョンの .NET Framework では、オフライン アプリケーションの場合に `-providerUrl` を除外すると、エラーになります。\)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  配置マニフェストに署名しないでください。  
  
8.  顧客にすべてのファイルを提供します。顧客はアプリケーションをネットワーク上に配置します。  
  
9. この時点で、顧客は自分で生成した証明書を使用して配置マニフェストに署名する必要があります。  たとえば、顧客が Adventure Works という会社の従業員である場合、顧客は MakeCert.exe ツールを使用して自己署名証明書を生成できます。  次に Pvk2pfx.exe ツールを使用して、MakeCert.exe によって作成されたファイルを、Mage.exe に渡すことができる PFX ファイルに結合します。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. 次に顧客は、この証明書を使用して配置マニフェストに署名します。  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. 顧客がユーザーにアプリケーションを配置します。  
  
### 複数の配置および商標をサポートする ClickOnce アプリケーションを MageUI.exe を使用して配置するには  
  
1.  Visual Studio コマンド プロンプトまたは [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] のコマンド プロンプトを開き、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] のファイルを格納するディレクトリに移動します。  
  
2.  bin サブディレクトリを作成し、実行可能ファイル、アセンブリ、リソース ファイル、データ ファイルなど、すべてのアプリケーション ファイルをこのサブディレクトリにコピーします。  
  
3.  サブディレクトリを作成し、配置の現在のバージョンに対応させて名前を付けます。  初めてアプリケーションを配置する場合であれば、1.0.0.0 などの名前を付けます。  
  
    > [!NOTE]
    >  配置のバージョンは、アプリケーション ファイルのバージョンとは異なる場合もあります。  
  
4.  \\bin ディレクトリを手順 2. で作成したディレクトリに移動します。  
  
5.  グラフィカル ツールの MageUI.exe を起動します。  
  
    ```  
    MageUI.exe  
    ```  
  
6.  **\[File\]** メニューの **\[New\]** をポイントし、**\[Application Manifest\]** をクリックして、アプリケーション マニフェストを新規作成します。  
  
7.  既定で表示される **\[Name\]** ページで、この配置の名前およびバージョン番号を入力します。  **\[Publisher\]** の値も指定します。この値は、配置時の \[スタート\] メニューで、アプリケーションのショートカット リンクのフォルダー名として使用されます。  
  
8.  **\[Application Options\]** タブをクリックし、**\[Use Application Manifest for Trust Information\]** をクリックします。  これにより、この [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションにサードパーティの商標を使用できるようになります。  
  
9. **\[Files\]** タブをクリックし、\[Application Directory\] ボックスの横の **\[Browse\]** をクリックします。  
  
10. フォルダー選択ダイアログ ボックスで、アプリケーション ファイルが格納されている、手順 2. で作成したディレクトリを選択し、**\[OK\]** をクリックします。  
  
11. **\[Populate\]** をクリックし、アプリケーション ファイルすべてをファイル リストに追加します。  アプリケーションに実行可能ファイルが複数含まれている場合は、**\[File Type\]** ボックスの **\[Entry Point\]** をオンにして、この配置のメイン実行可能ファイルをスタートアップ アプリケーションとして指定します。  アプリケーションの実行可能ファイルが 1 つだけの場合には、そのファイルが MageUI.exe によってメイン実行可能ファイルとしてマークされます。  
  
12. **\[Permissions Required\]** タブをクリックし、アプリケーションが要求する信頼のレベルを選択します。  既定値は **\[Full Trust\]** です。この設定は、ほとんどのアプリケーションに適しています。  
  
13. **\[File\]** メニューの **\[Save\]** をクリックし、アプリケーション マニフェストを保存します。  保存すると、アプリケーション マニフェストへの署名を求めるメッセージが表示されます。  
  
14. 証明書をファイルとしてファイル システムに保存してある場合には、**\[Sign as certificate file\]** オプションの省略記号 \(**\[...\]**\) ボタンをクリックして、ファイル システム上の証明書を選択します。  
  
     または  
  
     使用しているコンピューターからアクセスできる証明書ストアに証明書が保存されている場合には、**\[Sign with stored certificate option\]** をクリックし、表示された一覧から証明書を選択します。  
  
15. **\[File\]** メニューの **\[New\]** をポイントし、**\[Deployment Manifest\]** をクリックして、配置マニフェストを作成します。次に、**\[Name\]** ページで名前とバージョン番号 \(この例の場合は、1.0.0.0\) を入力します。  
  
16. **\[Update\]** タブをクリックし、このアプリケーションを更新する頻度を指定します。  アプリケーションで [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 配置 API を使用して自動的に更新プログラムをチェックする場合には、**\[This application should check for updates\]** チェック ボックスをオフにします。  
  
17. **\[Application Reference\]** タブに移動します。  **\[Select Manifest\]** をクリックし、前の手順で作成したアプリケーション マニフェストを選択すると、このページに表示されるすべての値に初期値を入力できます。  
  
18. **\[Save\]** をクリックし、配置マニフェストをディスクに保存します。  保存すると、アプリケーション マニフェストへの署名を求めるメッセージが表示されます。  **\[Cancel\]** をクリックすると、署名なしでマニフェストが保存されます。  
  
19. すべてのアプリケーション ファイルを顧客に提供します。  
  
20. この時点で、顧客は自分で生成した証明書を使用して配置マニフェストに署名する必要があります。  たとえば、顧客が Adventure Works という会社の従業員である場合、顧客は MakeCert.exe ツールを使用して自己署名証明書を生成できます。  次に Pvk2pfx.exe ツールを使用して、MakeCert.exe によって作成されたファイルを、MageUI.exe に渡すことができる PFX ファイルに結合します。  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. 証明書が生成されたら、顧客は MageUI.exe で配置マニフェストを開いて配置マニフェストに署名し、署名した配置マニフェストを保存します。  署名ダイアログ ボックスが表示されたら、顧客は **\[Sign as certificate file\]** をクリックし、ディスクに保存した PFX ファイルを選択します。  
  
22. 顧客がユーザーにアプリケーションを配置します。  
  
## 次の手順  
  
## 参照  
 [Mage.exe \(マニフェストの生成および編集ツール\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(マニフェスト生成および編集ツールのグラフィカル クライアント\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe \(証明書作成ツール\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)