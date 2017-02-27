---
title: "&lt;InstallChecks&gt; 要素 (ブートストラップ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<InstallChecks> 要素 [ブートストラップ]"
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# &lt;InstallChecks&gt; 要素 (ブートストラップ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`InstallChecks` 要素は、アプリケーションのための適切な必須コンポーネントがローカル コンピューターにインストール済みであるかどうかを確認する各種テストの起動をサポートします。  
  
## 構文  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## AssemblyCheck  
 この要素は、`InstallChecks` の子要素で、省略可能です。  ブートストラップは、`AssemblyCheck` の各インスタンスについて、この要素で指定されたアセンブリがグローバル アセンブリ キャッシュ \(GAC\) に存在するかどうかを確認します。  要素はなく、次の属性を持ちます。  
  
|属性|Description|  
|--------|-----------------|  
|`Property`|必ず指定します。  結果を格納するプロパティの名前です。  このプロパティは `InstallConditions` 要素に従って行われるテストから参照できます。この要素は、`Command` 要素の子です。  詳細については、「[\<Commands\> 要素](../deployment/commands-element-bootstrapper.md)」を参照してください。|  
|`Name`|必ず指定します。  チェック対象のアセンブリの完全修飾名です。|  
|`PublicKeyToken`|必ず指定します。  この厳密な名前を持つアセンブリに関連付けられている公開キーの省略形です。  GAC に格納するアセンブリには、名前、バージョン、および公開キーが必要です。|  
|`Version`|必ず指定します。  アセンブリのバージョンです。<br /><br /> バージョン番号の形式は、\<*major version*\>.\<*minor version*\>.\<*build version*\>.\<*revision version*\> です。|  
|`Language`|省略可能です。  ローカライズ済みアセンブリの言語です。  既定値は `neutral` です。|  
|`ProcessorArchitecture`|省略可能です。  このインストールの対象のコンピューター プロセッサです。  既定値は `msil` です。|  
  
## ExternalCheck  
 この要素は、`InstallChecks` の子要素で、省略可能です。  ブートストラップでは、`ExternalCheck` の各インスタンスについて、指定した外部プログラムが個別のプロセスで実行され、`Property` が示すプロパティに終了コードが格納されます。  `ExternalCheck` は、複雑な依存性チェックを実装する場合や、コンポーネントの存在をチェックする唯一の方法がインスタンス化の場合に便利です。  
  
 `ExternalCheck` に要素はなく、次の属性を持ちます。  
  
|属性|Description|  
|--------|-----------------|  
|`Property`|必ず指定します。  結果を格納するプロパティの名前です。  このプロパティは `InstallConditions` 要素に従って行われるテストから参照できます。この要素は、`Command` 要素の子です。  詳細については、「[\<Commands\> 要素](../deployment/commands-element-bootstrapper.md)」を参照してください。|  
|`PackageFile`|必ず指定します。  実行する外部プログラムです。  このプログラムは、セットアップ配布パッケージに含まれている必要があります。|  
|`Arguments`|省略可能です。  `PackageFile` で指定した実行可能ファイルのコマンド ライン引数を指定します。|  
  
## FileCheck  
 この要素は、`InstallChecks` の子要素で、省略可能です。  ブートストラップでは、`FileCheck` のインスタンスごとに、指定されたファイルが存在するかどうかを確認し、ファイルのバージョン番号を返します。  ファイルにバージョン番号がない場合、`Property` で指定したプロパティには 0 が設定されます。  ファイルが存在しない場合、`Property` に値は設定されません。  
  
 `FileCheck` に要素はなく、次の属性を持ちます。  
  
|属性|Description|  
|--------|-----------------|  
|`Property`|必ず指定します。  結果を格納するプロパティの名前です。  このプロパティは `InstallConditions` 要素に従って行われるテストから参照できます。この要素は、`Command` 要素の子です。  詳細については、「[\<Commands\> 要素](../deployment/commands-element-bootstrapper.md)」を参照してください。|  
|`FileName`|必ず指定します。  検索するファイルの名前です。|  
|`SearchPath`|必ず指定します。  ファイルを検索するディスクまたはフォルダーです。  `SpecialFolder` が割り当てられている場合は相対パスで、それ以外の場合は絶対パスで指定する必要があります。|  
|`SpecialFolder`|省略可能です。  Windows または [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] にとって特に重要なフォルダーです。  既定値は、`SearchPath` を絶対パスと解釈したパスです。  以下の値が有効です。<br /><br /> `AppDataFolder`。  この [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションのアプリケーション データ フォルダーです。現在のユーザーに固有です。<br /><br /> `CommonAppDataFolder`。  すべてのユーザーが使用するアプリケーション データ フォルダーです。<br /><br /> `CommonFilesFolder`。  現在のユーザー用の共有ファイル フォルダーです。<br /><br /> `LocalDataAppFolder`。  非ローミング アプリケーション用のデータ フォルダーです。<br /><br /> `ProgramFilesFolder`。  32 ビット アプリケーション用の標準の Program Files フォルダーです。<br /><br /> `StartUpFolder`。  システム起動時に開始されるすべてのアプリケーションを格納するフォルダーです。<br /><br /> `SystemFolder`。  32 ビット システム DLL を格納するフォルダーです。<br /><br /> `WindowsFolder`。  Windows システムのインストール フォルダーです。<br /><br /> `WindowsVolume`。  Windows システムのインストール ドライブまたはパーティションです。|  
|`SearchDepth`|省略可能です。  指定したファイルを検索するサブフォルダーの階層の深さです。  検索は、深さ優先で行われます。  既定値は 0 です。この場合、`SpecialFolder` および **SearchPath** で直接指定してあるフォルダーだけが検索されます。|  
  
## MsiProductCheck  
 この要素は、`InstallChecks` の子要素で、省略可能です。  ブートストラップでは、`MsiProductCheck` のインスタンスごとに、指定された Microsoft Windows インストーラーのインストールが最後まで実行されているかどうかを確認します。  プロパティ値は、製品のインストール状態に基づいて設定されます。  正の値は製品がインストールされていることを示し、0 または \-1 はインストールされていないことを示します   \(詳細については、Windows インストーラー SDK の MsiQueryFeatureState 関数を参照してください\)。.  Windows インストーラーがコンピューターにインストールされていない場合は、`Property` が設定されません。  
  
 `MsiProductCheck` に要素はなく、次の属性を持ちます。  
  
|属性|Description|  
|--------|-----------------|  
|`Property`|必ず指定します。  結果を格納するプロパティの名前です。  このプロパティは `InstallConditions` 要素に従って行われるテストから参照できます。この要素は、`Command` 要素の子です。  詳細については、「[\<Commands\> 要素](../deployment/commands-element-bootstrapper.md)」を参照してください。|  
|`Product`|必ず指定します。  インストールされる製品の GUID です。|  
|`Feature`|省略可能です。  インストールするアプリケーションの特定の機能に対する GUID です。|  
  
## RegistryCheck  
 この要素は、`InstallChecks` の子要素で、省略可能です。  ブートストラップでは、`RegistryCheck` のインスタンスごとに、指定されたレジストリ キーが存在するかどうか、または、そのレジストリ キーに指定された値が設定されているかどうかを確認します。  
  
 `RegistryCheck` に要素はなく、次の属性を持ちます。  
  
|属性|Description|  
|--------|-----------------|  
|`Property`|必ず指定します。  結果を格納するプロパティの名前です。  このプロパティは `InstallConditions` 要素に従って行われるテストから参照できます。この要素は、`Command` 要素の子です。  詳細については、「[\<Commands\> 要素](../deployment/commands-element-bootstrapper.md)」を参照してください。|  
|`Key`|必ず指定します。  レジストリ キーの名前です。|  
|`Value`|省略可能です。  取得するレジストリ値の名前です。  既定では既定値のテキストが返されます。  `Value` は、String または DWORD である必要があります。|  
  
## RegistryFileCheck  
 この要素は、`InstallChecks` の子要素で、省略可能です。  ブートストラップでは、`RegistryFileCheck` のインスタンスごとに、指定されたレジストリ キーからファイルのパスを取得し、指定されたファイルのバージョンを取得します。  この機能は、検索対象のファイルを格納してあるディレクトリが、レジストリ内に値として指定されている場合に、特に便利です。  
  
 `RegistryFileCheck` に要素はなく、次の属性を持ちます。  
  
|属性|Description|  
|--------|-----------------|  
|`Property`|必ず指定します。  結果を格納するプロパティの名前です。  このプロパティは `InstallConditions` 要素に従って行われるテストから参照できます。この要素は、`Command` 要素の子です。  詳細については、「[\<Commands\> 要素](../deployment/commands-element-bootstrapper.md)」を参照してください。|  
|`Key`|必ず指定します。  レジストリ キーの名前です。  `File` 属性が設定されていない場合には、この値がファイルのパスとして解釈されます。  このキーが存在しない場合、`Property` は設定されません。|  
|`Value`|省略可能です。  取得するレジストリ値の名前です。  既定では既定値のテキストが返されます。  `Value` は String である必要があります。|  
|`FileName`|省略可能です。  ファイルの名前です。  指定した場合には、レジストリ キーから取得した値をディレクトリ パスと仮定し、この名前をそのパスに追加します。  指定しなかった場合には、レジストリから取得した値を、ファイルへの完全パスであると仮定します。|  
|`SearchDepth`|省略可能です。  指定したファイルを検索するサブフォルダーの階層の深さです。  検索は、深さ優先で行われます。  既定値は 0 です。この場合は、レジストリ キーの値で直接指定したフォルダーだけが検索されます。|  
  
## 解説  
 実行するテストは、`InstallChecks` の子要素に定義しますが、これらの子要素でテストが実行されるわけではありません。  テストを実行するには、`Commands` 要素の下に `Command` 要素を作成する必要があります。  
  
## 使用例  
 次のコード例は、[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の製品ファイルで使用する場合の `InstallChecks` 要素を示しています。  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## InstallConditions  
 `InstallChecks` が評価されると、プロパティが生成されます。  これらのプロパティは `InstallConditions` で使用され、パッケージをインストールするか、バイパスするか、またはパッケージが失敗するかが判断されます。  次の表は、`InstallConditions` の一覧です。  
  
|||  
|-|-|  
|`FailIf`|いずれかの `FailIf` 条件が true になると、パッケージは失敗します。  残りの条件は評価されません。|  
|`BypassIf`|いずれかの `BypassIf` 条件が true になると、パッケージはバイパスされます。  残りの条件は評価されません。|  
  
## 定義済みプロパティ  
 次の表は、`BypassIf` 要素および `FailIf` 要素の一覧です。  
  
|プロパティ|説明|使用される値|  
|-----------|--------|------------|  
|`Version9X`|Windows 9X オペレーティング システムのバージョン番号。|4.10 \= Windows 98|  
|`VersionNT`|Windows NT ベースのオペレーティング システムのバージョン番号。|メジャー.マイナー.サービスパック<br /><br /> 5.0 \= Windows 2000<br /><br /> 5.1.0 \= Windows XP<br /><br /> 5.1.2 \= Windows XP Professional SP2<br /><br /> 5.2.0 \= Windows Server 2003|  
|`VersionNT64`|Windows NT ベースの 64 ビット オペレーティング システムのバージョン番号。|上記と同じ。|  
|`VersionMsi`|Windows インストーラー サービスのバージョン番号。|2.0 \= Windows インストーラー 2.0|  
|`AdminUser`|ユーザーが Windows NT ベースのオペレーティング システムの管理者特権を持っているかどうかを指定します。|0 \= 管理者特権なし<br /><br /> 1 \= 管理者特権あり|  
  
 たとえば、Windows 95 を実行するコンピューターへのインストールをブロックするには、次のようなコードを使用します。  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## 参照  
 [\<Commands\> 要素](../deployment/commands-element-bootstrapper.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)