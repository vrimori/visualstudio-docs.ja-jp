---
title: "方法 : ビルド イベントを指定する (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ビルド イベント [Visual Studio]"
  - "ビルド [Visual Studio], イベント"
  - "イベント [Visual Studio], ビルド"
  - "ビルド後のイベント"
  - "ビルド前のイベント"
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# 方法 : ビルド イベントを指定する (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ビルド イベントを使って、ビルドの開始前またはビルドの終了後に実行するコマンドを指定できます。  ビルド イベントは、ビルド処理でこれらのポイントにビルドが正常に到達した場合にだけ実行されます。  
  
 プロジェクトをビルドすると、ビルド前のイベントは PreBuildEvent.bat というファイルに追加され、ビルド後のイベントは PostBuildEvent.bat というファイルに追加されます。  エラー チェックを確実に行う場合は、独自のエラー チェック コマンドをビルド ステップに追加してください。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## ビルド前のイベントおよびビルド後のイベントの指定方法  
  
#### ビルド イベントを指定するには  
  
1.  **ソリューション エクスプローラー**で、ビルド イベントを指定するプロジェクトを選択します。  
  
2.  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
3.  **\[ビルド イベント\]** タブをクリックします。  
  
4.  **\[ビルド前に実行するコマンド ライン\]** ボックスで、ビルド イベントの構文を指定します。  
  
    > [!NOTE]
    >  ビルド前のイベントは、プロジェクトが最新の状態で、ビルドが発生しない場合には実行しません。  
  
5.  **\[ビルド後に実行するコマンド ライン\]** ボックスで、ビルド イベントの構文を指定します。  
  
    > [!NOTE]
    >  .bat ファイルを実行するすべてのビルド後コマンドの前に、`call` ステートメントを追加します。  たとえば、`call C:\MyFile.bat` または `call C:\MyFile.bat call C:\MyFile2.bat` です。  
  
6.  **\[ビルド後のコマンド ラインの実行条件\]** ボックスで、ビルド後のイベントを実行する条件を指定します。  
  
    > [!NOTE]
    >  長い構文を追加したり、[\[ビルド前に実行するコマンド ライン\] \/ \[ビルド後に実行するコマンド ライン\] ダイアログ ボックス](../Topic/Pre-build%20Event-Post-build%20Event%20Command%20Line%20Dialog%20Box.md)からビルド マクロを選択するには、省略記号ボタン \(**...**\) をクリックして編集ボックスを表示します。  
  
     ビルド イベントの構文には、コマンド プロンプトまたは .bat ファイルで有効な任意のコマンドを含めることができます。  バッチ ファイルの名前の先頭に `call` を付けて、すべての後続コマンドが実行されるようにする必要があります。  
  
     **メモ** ビルド前のイベントまたはビルド後のイベントが正常に完了しなかった場合は、ゼロ \(0 はアクションの成功を示す\) 以外のコードでイベント アクションを終了させることによって、ビルドを強制終了できます。  
  
## 例 : ビルド後のイベントを使用してマニフェスト情報を変更する方法  
 次の手順は、ビルド後のイベントから呼び出される .exe コマンドを使用して、アプリケーション マニフェスト \(プロジェクト ディレクトリ内の .exe.manifest ファイル\) 内にオペレーティング システムの最小バージョンを設定する方法を示しています。  オペレーティング システムの最小バージョンは、4.10.0.0 などの 4 つの部分に分かれた数字です。  これを行うには、コマンドでマニフェストの `<dependentOS>` セクションを変更します。  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### アプリケーション マニフェストを変更する .exe コマンドを作成するには  
  
1.  コマンド用のコンソール アプリケーションを作成します。  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[Visual C\#\]** を展開し、**\[Windows\]** をクリックして、**\[コンソール アプリケーション\]** テンプレートをクリックします。  プロジェクトに「`ChangeOSVersionCS`」という名前を付けます。  
  
3.  Program.cs で、ファイルの先頭にある他の `using` ステートメントに加えて次の行を記述します。  
  
    ```  
    using System.Xml;  
    ```  
  
4.  `ChangeOSVersionCS` 名前空間で、`Program` クラスの実装を次のコードに置き換えます。  
  
    ```  
    class Program  
    {  
       /// <summary>  
       /// This function will set the minimum operating system version for a ClickOnce application.  
       /// </summary>  
       /// <param name="args">  
       /// Command Line Arguments:  
       /// 0 - Path to application manifest (.exe.manifest).  
       /// 1 - Version of OS  
       ///</param>  
       static void Main(string[] args)  
       {  
          string applicationManifestPath = args[0];  
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
          // Get version name.  
          Version osVersion = null;  
          if (args.Length >=2 ){  
             osVersion = new Version(args[1]);  
          }else{  
             throw new ArgumentException("OS Version not specified.");  
          }  
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
          XmlDocument document;  
          XmlNamespaceManager namespaceManager;  
          namespaceManager = new XmlNamespaceManager(new NameTable());  
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
          document = new XmlDocument();  
          document.Load(applicationManifestPath);  
  
          string baseXPath;  
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
          // Change minimum required operating system version.  
          XmlNode node;  
          node = document.SelectSingleNode(baseXPath, namespaceManager);  
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
          document.Save(applicationManifestPath);  
       }  
    }  
    ```  
  
     このコマンドは、引数として、アプリケーション マニフェストのパス \(つまり、ビルド処理によってマニフェストが作成されるフォルダー。通常は Projectname.publish\) と、設定するオペレーティング システムのバージョンを受け取ります。  
  
5.  プロジェクトをビルドします。  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
6.  .exe ファイルを `C:\TEMP\ChangeOSVersionVB.exe` などのディレクトリにコピーします。  
  
 次に、ビルド後のイベントでこのコマンドを起動して、アプリケーション マニフェストを変更します。  
  
#### ビルド後のイベントを起動してアプリケーション マニフェストを変更するには  
  
1.  発行するプロジェクト用 Windows アプリケーションを作成します。  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[Visual C\#\]** を展開し、**\[Windows\]** をクリックして、**\[Windows フォーム アプリケーション\]** テンプレートをクリックします。  プロジェクトに「`CSWinApp`」という名前を付けます。  
  
3.  ソリューション エクスプローラーでプロジェクトが選択されている状態で、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
4.  プロジェクト デザイナーで、**\[発行\]** ページに移動し、**\[発行場所\]** を `C:\TEMP\` に設定します。  
  
5.  **\[今すぐ発行\]** をクリックしてプロジェクトを発行します。  
  
     マニフェスト ファイルがビルドされ、`C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest` に配置されます。  マニフェストを表示するには、ファイルを右クリックし、**\[プログラムから開く\]** をポイントします。次に、**\[一覧からプログラムを選択する\]** をクリックし、**\[Notepad\]** をクリックします。  
  
     ファイルで `<osVersionInfo>` 要素を探します。  たとえば、バージョンは次のように記述されています。  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  プロジェクト デザイナーで、**\[ビルド イベント\]** タブをクリックし、**\[ビルド後の編集\]** をクリックします。  
  
7.  **\[ビルド後に実行するコマンド ライン\]** ボックスで、次のコマンドを入力します。  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     プロジェクトをビルドすると、このコマンドによってアプリケーション マニフェスト内のオペレーティング システムの最小バージョンが 5.1.2600.0 に変更されます。  
  
     `$(TargetPath)` マクロは、作成される実行可能ファイルへの完全パスを表すため、`$(TargetPath)`.manifest と記述すると、bin ディレクトリに作成されたアプリケーション マニフェストを指定することになります。  発行することにより、前に設定した発行場所にこのマニフェストがコピーされます。  
  
8.  プロジェクトを再び発行します。  **\[発行\]** ページに移動し、**\[今すぐ発行\]** をクリックします。  
  
     マニフェストを再び表示します。  マニフェストを表示するには、発行ディレクトリを開き、ファイルを右クリックして、**\[プログラムから開く\]** をポイントします。次に、**\[一覧からプログラムを選択する\]** をクリックし、**\[Notepad\]** をクリックします。  
  
     設定したバージョンが表示されます。  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## 参照  
 [\[ビルド イベント\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Events%20Page,%20Project%20Designer%20\(C%23\).md)   
 [\[ビルド前に実行するコマンド ライン\] \/ \[ビルド後に実行するコマンド ライン\] ダイアログ ボックス](../Topic/Pre-build%20Event-Post-build%20Event%20Command%20Line%20Dialog%20Box.md)   
 [方法 : ビルド イベントを指定する \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Visual Studio でのアプリケーションのビルド](../ide/compiling-and-building-in-visual-studio.md)