---
title: "&lt;Commands&gt; 要素 (ブートストラップ) | Microsoft Docs"
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
  - "<Commands> 要素 [ブートストラップ]"
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;Commands&gt; 要素 (ブートストラップ)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Commands` 要素は、`InstallChecks` 要素の下の要素で記述されているテストを実装し、テストが失敗した場合に [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ブートストラップによってインストールされる必要のあるパッケージを宣言します。  
  
## 構文  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## 要素と属性  
 `Commands` 要素は必須です。   要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Reboot`|省略可能です。  いずれかのパッケージから再起動を示す終了コードが返された場合に、システムを再起動する必要があるかどうかを指定します。  有効な値は次のとおりです。<br /><br /> `Defer`。  再起動をしばらく延期します。<br /><br /> `Immediate`。  いずれかのパッケージから再起動を示す終了コードが返された場合は、すぐに再起動します。<br /><br /> `None`。  再起動の要求を無視します。<br /><br /> 既定値は `Immediate` です。|  
  
## コマンド  
 `Command` 要素は、`Commands` 要素の子要素です。  `Commands` 要素は `Command` 要素を 1 つ以上持つことができます。  この要素には、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`PackageFile`|必ず指定します。  `InstallConditions` で指定された条件の 1 つ以上で false が戻ったときに、インストールする必要のあるパッケージの名前です。  このパッケージは、`PackageFile` 要素を使用して、同じファイル内で定義されている必要があります。|  
|`Arguments`|省略可能です。  パッケージ ファイルに渡す一連のコマンド ライン引数です。|  
|`EstimatedInstallSeconds`|省略可能です。  パッケージのインストールに必要な時間 \(秒単位\) の予想値です。  この値によって、ブートストラップがユーザーに表示するプログレス バーのサイズが決まります。  既定値は 0 です。この場合、予想時間は指定されません。|  
|`EstimatedDiskBytes`|省略可能です。  インストール完了後にパッケージによって占有される総ディスク容量 \(バイト単位\) の予想値です。  この値は、ブートストラップがユーザーに表示するディスク容量の要件として使用されます。  既定値は 0 です。この場合、ブートストラップでは、ディスク容量の要件が表示されません。|  
|`EstimatedTempBytes`|省略可能です。  パッケージに必要な、一時ディスク容量 \(バイト単位\) の予想値です。|  
|`Log`|省略可能です。  パッケージが作成するログ ファイルのパスを、パッケージのルート ディレクトリからの相対ディレクトリで指定します。|  
  
## InstallConditions  
 `InstallConditions` 要素は、`Command` 要素に必須の子です。  各 `Command` 要素は、1 つ以上の `InstallConditions` 要素を持つことができます。  `InstallConditions` 要素が存在しない場合、`Condition` で指定されたパッケージが常に実行されます。  
  
## BypassIf  
 `BypassIf` 要素は `InstallConditions` 要素の子要素です。コマンドを実行しない場合の肯定条件を記述します。  各 `InstallConditions` 要素は、`BypassIf` 要素を 0 個以上持つことができます。  
  
 `BypassIf` には、以下の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Property`|必ず指定します。  テストするプロパティの名前です。  プロパティは、`InstallChecks` 要素の子要素によって、あらかじめ定義されている必要があります。  詳細については、「[\<InstallChecks\> 要素](../deployment/installchecks-element-bootstrapper.md)」を参照してください。|  
|`Compare`|必ず指定します。  実行する比較の種類です。  有効な値は次のとおりです。<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必ず指定します。  プロパティと比較する値です。|  
|`Schedule`|省略可能です。  この規則をいつ評価するのかを定義する `Schedule` タグの名前です。|  
  
## FailIf  
 `FailIf` 要素は `InstallConditions` 要素の子要素です。インストールを中止する肯定条件を記述します。  各 `InstallConditions` 要素は、`FailIf` 要素を 0 個以上持つことができます。  
  
 `FailIf` には、以下の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Property`|必ず指定します。  テストするプロパティの名前です。  プロパティは、`InstallChecks` 要素の子要素によって、あらかじめ定義されている必要があります。  詳細については、「[\<InstallChecks\> 要素](../deployment/installchecks-element-bootstrapper.md)」を参照してください。|  
|`Compare`|必ず指定します。  実行する比較の種類です。  有効な値は次のとおりです。<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必ず指定します。  プロパティと比較する値です。|  
|`String`|省略可能です。  失敗時にユーザーに表示するテキストです。|  
|`Schedule`|省略可能です。  この規則をいつ評価するのかを定義する `Schedule` タグの名前です。|  
  
## ExitCodes  
 `ExitCodes` 要素は、`Command` 要素に必須の子です。  `ExitCodes` 要素は、パッケージの終了コードに応じてインストールが実行する内容を指定する 1 つ以上の `ExitCode` 要素を含みます。  `Command` 要素の下には、オプションで 1 個の `ExitCode` 要素を指定できます。  `ExitCodes` に属性はありません。  
  
## ExitCode  
 `ExitCode` 要素は、`ExitCodes` 要素に必須の子です。  `ExitCode` 要素には、パッケージの終了コードに応じてインストールが実行する内容を指定します。  `ExitCode` に子要素はなく、次の属性があります。  
  
|属性|Description|  
|--------|-----------------|  
|`Value`|必ず指定します。  この `ExitCode` 要素を適用する終了コード値です。|  
|`Result`|必ず指定します。  この終了コードに対応するインストーラーの処理を指定します。  有効な値は次のとおりです。<br /><br /> `Success`。  正常にインストールされたことを示すフラグをパッケージに付けます。<br /><br /> `SuccessReboot`。  正常にインストールされたことを示すフラグをパッケージに付け、再起動するようにシステムに指示します。<br /><br /> `Fail`。  インストールが失敗したことを示すフラグをパッケージに付けます。<br /><br /> `FailReboot`。  インストールが失敗したことを示すフラグをパッケージに付け、再起動するようにシステムに指示します。|  
|`String`|省略可能です。  この終了コードに対応して、ユーザーに表示する文字列を指定します。|  
|`FormatMessageFromSystem`|省略可能です。  この終了コードに対応する、システムで用意されているエラー メッセージを表示するのか、`String` に指定した値を使用するのかを指定します。  有効な値は、`true` \(システムで用意されているエラーを使用\) および `false` \(`String` に指定した値を使用\) です。  既定値は `false` です。  このプロパティが `false` で、`String` が設定されていない場合、システムが提供するエラーが使用されます。|  
  
## 使用例  
 .NET Framework 2.0 をインストールするためのコマンドを定義するコード例を次に示します。  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## 参照  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks\> 要素](../deployment/installchecks-element-bootstrapper.md)