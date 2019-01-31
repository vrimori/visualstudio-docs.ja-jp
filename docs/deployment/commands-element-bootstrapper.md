---
title: '&lt;コマンド&gt;要素 (ブートス トラップ) |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eab1e5d8ab9a4e1644c8eb1a99d1aab4fdf6d9e0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928075"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;コマンド&gt;要素 (ブートス トラップ)
`Commands`要素は、テストの下にある要素の説明を実装、`InstallChecks`要素と、パッケージを宣言し、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]テストが失敗した場合、ブートス トラップをインストールする必要があります。  
  
## <a name="syntax"></a>構文  
  
```xml  
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
  
## <a name="elements-and-attributes"></a>要素と属性  
 `Commands`要素が必要です。 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Reboot`|任意。 再起動終了コードを返さない、パッケージのいずれかの場合、システムを再起動する必要があるかどうかを判断します。 次に、有効な値を示します。<br /><br /> `Defer`。 再起動は、いくつかの将来の時刻まで延期されます。<br /><br /> `Immediate`。 パッケージの 1 つ再起動終了コードが返される場合がすぐに再起動されます。<br /><br /> `None`。 再起動の要求を無視するとします。<br /><br /> 既定値は、`Immediate` です。|  
  
## <a name="command"></a>コマンド  
 `Command` 要素は、`Commands` 要素の子要素です。 A`Commands`要素は、1 つ以上を持つことができます`Command`要素。 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`PackageFile`|必須です。 インストールするパッケージの名前は、指定した条件の 1 つ以上必要があります。 `InstallConditions` false を返します。 使用して同じファイルでパッケージを定義する必要があります、`PackageFile`要素。|  
|`Arguments`|任意。 パッケージ ファイルに渡すコマンドライン引数のセット。|  
|`EstimatedInstallSeconds`|任意。 推定時間 (秒)、パッケージのインストールにかかります。 この値は、ブートス トラップがユーザーに表示する進行状況バーのサイズを決定します。 既定値は 0、後者推定値が指定されていない時間です。|  
|`EstimatedDiskBytes`|任意。 インストールした後、パッケージによって占有されるバイト単位でのディスク領域の推定量が完了しました。 この値は、ブートス トラップをユーザーに表示するディスク容量の要件で使用されます。 既定では 0、ハード_ディスク容量要件は、ブートス トラップの場合に表示されません。|  
|`EstimatedTempBytes`|任意。 パッケージが必要になるバイト単位での一時ディスク領域の推定量。|  
|`Log`|任意。 パッケージのルート ディレクトリに対して相対的なパッケージを生成するログ ファイルへのパス。|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions`要素の子である、`Command`要素。 各`Command`要素には、最大で 1 つを指定できる`InstallConditions`要素。 ない場合は`InstallConditions`要素が存在するによって指定されたパッケージ`Condition`は常に実行します。  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf`要素の子である、`InstallConditions`要素とするコマンドは実行されませんが、正の条件について説明します。 各`InstallConditions`0 個以上の要素を持つことができます`BypassIf`要素。  
  
 `BypassIf` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須です。 テストするプロパティの名前。 子でプロパティ以前おく必要があります、`InstallChecks`要素。 詳細については、次を参照してください。 [ \<InstallChecks > 要素](../deployment/installchecks-element-bootstrapper.md)します。|  
|`Compare`|必須です。 実行する比較の種類。 次に、有効な値を示します。<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必須です。 プロパティと比較する値。|  
|`Schedule`|任意。 名前、`Schedule`このルールを評価するときに定義するタグ。|  
  
## <a name="failif"></a>FailIf  
 `FailIf`要素の子である、`InstallConditions`要素と、インストールを停止する正の条件について説明します。 各`InstallConditions`0 個以上の要素を持つことができます`FailIf`要素。  
  
 `FailIf` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須です。 テストするプロパティの名前。 子でプロパティ以前おく必要があります、`InstallChecks`要素。 詳細については、次を参照してください。 [ \<InstallChecks > 要素](../deployment/installchecks-element-bootstrapper.md)します。|  
|`Compare`|必須です。 実行する比較の種類。 次に、有効な値を示します。<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必須です。 プロパティと比較する値。|  
|`String`|任意。 障害発生時にユーザーに表示するテキスト。|  
|`Schedule`|任意。 名前、`Schedule`このルールを評価するときに定義するタグ。|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes`要素の子である、`Command`要素。 `ExitCodes`要素は、1 つ以上含まれています。`ExitCode`要素で、インストールが終了コードをパッケージからの応答で行う必要がありますを決定します。 1 つできます省略可能な`ExitCode`下にある要素を`Command`要素。 `ExitCodes` に属性はありません。  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode`要素の子である、`ExitCodes`要素。 `ExitCode`要素は、インストールが終了コードをパッケージからの応答で行う必要がありますを決定します。 `ExitCode` 子要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Value`|必須です。 この終了コード値`ExitCode`要素に適用されます。|  
|`Result`|必須です。 どのインストールは、この終了コードに対応する必要があります。 次に、有効な値を示します。<br /><br /> `Success`。 正常にインストールされたパッケージのフラグを設定します。<br /><br /> `SuccessReboot`。 正常にインストールされた、パッケージのフラグを設定して、システムを再起動するように指示します。<br /><br /> `Fail`。 失敗したパッケージのフラグを設定します。<br /><br /> `FailReboot`。 失敗と、パッケージのフラグを設定し、システムを再起動するように指示します。|  
|`String`|任意。 この終了コードへの応答でユーザーに表示する値。|  
|`FormatMessageFromSystem`|任意。 終了コードに対応するシステム提供のエラー メッセージを使用するかで指定された値を使用するかどうかを判断します`String`します。 有効な値は`true`、システム指定のエラーを使用する場合はこれと`false`、によって提供される文字列を使用することを表す`String`します。 既定値は、`false` です。 このプロパティは、する場合`false`が`String`が設定された場合、システム指定のエラーが使用されます。|  
  
## <a name="example"></a>例  
 次のコード例では、.NET Framework 2.0 をインストールするためのコマンドを定義します。  
  
```xml  
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
  
## <a name="see-also"></a>関連項目  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > 要素](../deployment/installchecks-element-bootstrapper.md)