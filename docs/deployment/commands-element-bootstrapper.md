---
title: '&lt;コマンド&gt;要素 (ブートス トラップ) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac3ae61012bec5f8134a48714678110951c03b76
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;コマンド&gt;要素 (ブートス トラップ)
`Commands`テスト下にある要素の説明を実装する要素、`InstallChecks`要素、どのパッケージを宣言し、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]ブートス トラップがテストに失敗した場合にインストールする必要があります。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="elements-and-attributes"></a>要素と属性  
 `Commands`要素が必要です。 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Reboot`|任意。 再起動終了コードを返す任意のパッケージの場合、システムを再起動する必要があるかどうかを判断します。 次に、有効な値を示します。<br /><br /> `Defer`。 再起動がいくつかの将来の時刻まで遅延されます。<br /><br /> `Immediate`。 再起動終了コードが返されたパッケージのいずれかの場合は、即時再起動をさせます。<br /><br /> `None`。 無視するには、任意の再起動要求が発生します。<br /><br /> 既定値は、`Immediate` です。|  
  
## <a name="command"></a>コマンド  
 `Command` 要素は、`Commands` 要素の子要素です。 A`Commands`要素が 1 つ以上を持つ`Command`要素。 要素には、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`PackageFile`|必須。 インストールするパッケージの名前は、指定した条件の 1 つ以上必要があります。 `InstallConditions` false を返します。 パッケージを使用して、同じファイルで定義する必要があります、`PackageFile`要素。|  
|`Arguments`|任意。 パッケージ ファイルに渡すコマンドライン引数のセット。|  
|`EstimatedInstallSeconds`|任意。 推定時間 (秒)、パッケージをインストールするかかります。 この値は、ブートス トラップがユーザーに表示する進行状況バーのサイズを決定します。 既定値は 0、後者の見積もりが指定されていることはありません。|  
|`EstimatedDiskBytes`|任意。 インストールが完了したら、パッケージによって占有されるバイト数のディスク領域の予測サイズを終了します。 この値は、ハード ディスク領域要件をユーザーに表示する、ブートス トラップをで使用されます。 既定では 0、すべてのハード_ディスク空き容量はブートス トラップの場合に表示されません。|  
|`EstimatedTempBytes`|任意。 パッケージが必要になるバイト単位での一時ディスク領域の予測サイズです。|  
|`Log`|任意。 パッケージのルート ディレクトリに対して相対的なパッケージが作成されるログ ファイルへのパス。|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions`要素の子では、`Command`要素。 各`Command`要素には、1 つだけ持つことができます`InstallConditions`要素。 ない場合は`InstallConditions`要素が存在する、によって指定されたパッケージ`Condition`は常に実行します。  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf`要素の子では、`InstallConditions`要素とするコマンドは、実行してはならない正条件について説明します。 各`InstallConditions`要素が 0 以上を持つ`BypassIf`要素。  
  
 `BypassIf` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 テストするプロパティの名前。 プロパティ必要があります以前によって定義されているの子、`InstallChecks`要素。 詳細については、次を参照してください。 [ \<InstallChecks > 要素](../deployment/installchecks-element-bootstrapper.md)です。|  
|`Compare`|必須。 実行する比較の種類。 次に、有効な値を示します。<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必須。 プロパティと比較する値。|  
|`Schedule`|任意。 名前、`Schedule`この規則を評価するときを定義するタグです。|  
  
## <a name="failif"></a>FailIf  
 `FailIf`要素の子では、`InstallConditions`要素と、インストールを停止する正の値の条件について説明します。 各`InstallConditions`要素が 0 以上を持つ`FailIf`要素。  
  
 `FailIf` 次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 テストするプロパティの名前。 プロパティ必要があります以前によって定義されているの子、`InstallChecks`要素。 詳細については、次を参照してください。 [ \<InstallChecks > 要素](../deployment/installchecks-element-bootstrapper.md)です。|  
|`Compare`|必須。 実行する比較の種類。 次に、有効な値を示します。<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|必須。 プロパティと比較する値。|  
|`String`|任意。 エラー発生時にユーザーに表示するテキストです。|  
|`Schedule`|任意。 名前、`Schedule`この規則を評価するときを定義するタグです。|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes`要素の子では、`Command`要素。 `ExitCodes`要素は、1 つ以上含まれています。`ExitCode`要素を、インストールが終了コードをパッケージからの応答で行う必要がありますを指定します。 1 つできます省略可能な`ExitCode`要素の下に、`Command`要素。 `ExitCodes` 属性はありません。  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode`要素の子では、`ExitCodes`要素。 `ExitCode`要素は、インストールが終了コードをパッケージからの応答の実行を決定します。 `ExitCode` 子要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Value`|必須。 この終了コード値`ExitCode`要素に適用されます。|  
|`Result`|必須。 この終了コードをインストールする必要があります対処方法 次に、有効な値を示します。<br /><br /> `Success`。 正常にインストールされたパッケージのフラグを設定します。<br /><br /> `SuccessReboot`。 正常にインストールされたパッケージのフラグを設定し、システムを再起動するように指示します。<br /><br /> `Fail`。 パッケージのフラグを設定して、失敗します。<br /><br /> `FailReboot`。 失敗と、パッケージのフラグを設定し、システムを再起動するように指示します。|  
|`String`|任意。 この終了コードへの応答でユーザーに表示する値。|  
|`FormatMessageFromSystem`|任意。 終了コードに対応するシステム提供のエラー メッセージを使用またはで指定された値を使用するかどうかを判断`String`です。 有効な値は`true`、システム指定のエラーを使用していることを意味し、 `false`、によって提供される文字列を使用することを意味する`String`です。 既定値は、`false` です。 このプロパティは、する場合`false`が`String`が設定された場合、システム指定のエラーが使用されます。|  
  
## <a name="example"></a>例  
 次のコード例では、.NET Framework 2.0 をインストールするためのコマンドを定義します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > 要素](../deployment/installchecks-element-bootstrapper.md)