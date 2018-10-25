---
title: '&lt;InstallChecks&gt;要素 (ブートス トラップ) |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 03f489c22c8912e332f7d01e6ec4ac48aacda30b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891077"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt;要素 (ブートス トラップ)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`InstallChecks`要素のさまざまなアプリケーションの適切な前提条件のすべてがインストールされているかどうかを確認するローカル コンピューターに対するテストの開始をサポートしています。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="assemblycheck"></a>AssemblyCheck  
 この要素は省略可能な子要素の`InstallChecks`します。 インスタンスごとに`AssemblyCheck`、ブートス トラップが要素で指定されたアセンブリがグローバル アセンブリ キャッシュ (GAC) に存在することを確認してください。 要素が含まれていないと、次の属性があります。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)します。|  
|`Name`|必須。 チェック対象のアセンブリの完全修飾名。|  
|`PublicKeyToken`|必須。 公開キーの省略形は、このアセンブリの厳密な名前に関連付けられています。 GAC に格納されているすべてのアセンブリは、名前、バージョン、および公開キーが必要です。|  
|`Version`|必須。 アセンブリのバージョン。<br /><br /> バージョン番号が、形式\<*メジャー バージョン*>.\<*マイナー バージョン*>.\<*ビルド バージョン*>.\<*リビジョン バージョン*>。|  
|`Language`|任意。 ローカライズされたアセンブリの言語です。 既定値は `neutral` です。|  
|`ProcessorArchitecture`|任意。 このインストールの対象となるコンピューターのプロセッサ。 既定値は `msil` です。|  
  
## <a name="externalcheck"></a>ExternalCheck  
 この要素は省略可能な子要素の`InstallChecks`します。 インスタンスごとに`ExternalCheck`、ブートス トラップは別のプロセスで、名前付きの外部のプログラムを実行し、その終了コードで示されるプロパティに格納`Property`します。 `ExternalCheck` 複雑な依存関係のチェックを実装するため、またはコンポーネントの存在を確認する唯一の方法でインスタンス化する場合に便利です。  
  
 `ExternalCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)します。|  
|`PackageFile`|必須。 実行する外部プログラムです。 プログラムは、セットアップの配布パッケージの一部である必要があります。|  
|`Arguments`|任意。 実行可能ファイルによってという名前のコマンドライン引数を提供`PackageFile`します。|  
  
## <a name="filecheck"></a>チェックイン  
 この要素は省略可能な子要素の`InstallChecks`します。 インスタンスごとに`FileCheck`、ブートス トラップは、名前付きのファイルが存在し、ファイルのバージョン番号を返すかどうかが決まります。 ブートス トラップがによってという名前のプロパティを設定する場合は、ファイルには、バージョン番号がない、`Property`を 0 にします。 ファイルが存在しない場合`Property`任意の値に設定されていません。  
  
 `FileCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)します。|  
|`FileName`|必須。 検索するファイルの名前。|  
|`SearchPath`|必須。 ディスクまたはファイルを検索するフォルダー。 場合は、相対パスをあるこの必要があります`SpecialFolder`が割り当てられます。 それ以外の場合、その絶対パスである必要があります。|  
|`SpecialFolder`|任意。 Windows に、またはに特別な意味を持つフォルダー[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]します。 既定では解釈`SearchPath`に絶対パス。 以下の値が有効です。<br /><br /> `AppDataFolder`。 このアプリケーション データ フォルダー[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション; 現在のユーザーに特定します。<br /><br /> `CommonAppDataFolder`。 すべてのユーザーが使用するアプリケーション データ フォルダー。<br /><br /> `CommonFilesFolder`。 現在のユーザーの共通ファイル フォルダーです。<br /><br /> `LocalDataAppFolder`。 アプリケーションの非ローミングのデータ フォルダー。<br /><br /> `ProgramFilesFolder`。 32 ビット アプリケーションの標準の Program Files フォルダー。<br /><br /> `StartUpFolder`。 このフォルダーは、システムの起動時に起動されたすべてのアプリケーションが含まれています。<br /><br /> `SystemFolder`。 このフォルダーは、32 ビット システム Dll が含まれています。<br /><br /> `WindowsFolder`。 このフォルダーは、Windows システムのインストールが含まれています。<br /><br /> `WindowsVolume`。 ドライブまたはパーティションを Windows システムのインストールが含まれています。|  
|`SearchDepth`|任意。 名前付きのファイル用のサブフォルダーを検索する位置の深さ。 深さ優先検索では。 既定値は 0 であり、によって指定された最上位フォルダーの検索範囲を限定`SpecialFolder`と**SearchPath**します。|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 この要素は省略可能な子要素の`InstallChecks`します。 インスタンスごとに`MsiProductCheck`、ブートス トラップが完了するまでに指定した Microsoft Windows インストーラーのインストールが実行するかどうかを確認します。 プロパティの値は、製品のインストールの状態によって設定されます。 正の値は、製品がインストールされていることを示します。 0 または-1 がインストールされていないことを示します。 (を参照してください詳細については、Windows インストーラー SDK 関数 MsiQueryFeatureState。). Windows インストーラーがコンピューターにインストールされていない場合`Property`が設定されていません。  
  
 `MsiProductCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)します。|  
|`Product`|必須。 インストールされている製品の GUID です。|  
|`Feature`|任意。 インストールされているアプリケーションの特定の機能の GUID です。|  
  
## <a name="registrycheck"></a>RegistryCheck  
 この要素は省略可能な子要素の`InstallChecks`します。 インスタンスごとに`RegistryCheck`、ブートス トラップは、指定されたレジストリ キーが存在するかどうか、または、指定された値があるかどうかを確認します。  
  
 `RegistryCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)します。|  
|`Key`|必須。 レジストリ キーの名前。|  
|`Value`|任意。 取得するレジストリ値の名前。 既定では、既定値のテキストを返します。 `Value` DWORD または文字列のいずれかである必要があります。|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 この要素は省略可能な子要素の`InstallChecks`します。 インスタンスごとに`RegistryFileCheck`、ブートス トラップは最初に指定されたレジストリ キーからファイルへのパスを取得しようとすると、指定されたファイルのバージョンを取得します。 これは、レジストリの値として指定されたディレクトリ内のファイルを検索する場合に特に便利です。  
  
 `RegistryFileCheck` 要素が含まれていない、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`Property`|必須。 結果を格納するプロパティの名前。 このプロパティは、下にテストから参照できる、`InstallConditions`子である要素の`Command`要素。 詳細については、次を参照してください。 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)します。|  
|`Key`|必須。 レジストリ キーの名前。 しない限り、その値は、ファイルへのパスとして解釈されます、`File`属性を設定します。 このキーが存在しない場合`Property`が設定されていません。|  
|`Value`|任意。 取得するレジストリ値の名前。 既定では、既定値のテキストを返します。 `Value` 文字列である必要があります。|  
|`FileName`|任意。 ファイルの名前。 指定すると、レジストリ キーから取得した値と見なされます、ディレクトリ パスを指定して、この名前が追加されました。 指定しない場合、レジストリから返される値は、ファイルへの完全パスと見なされます。|  
|`SearchDepth`|任意。 名前付きのファイル用のサブフォルダーを検索する位置の深さ。 深さ優先検索では。 既定では 0 で、レジストリ キーの値によって指定された最上位のフォルダーに検索が制限されます。|  
  
## <a name="remarks"></a>Remarks  
 下にある要素の中に`InstallChecks`を実行するテストを定義して、それらが実行しないでください。 作成する必要があります、テストを実行する`Command`要素の下に、`Commands`要素。  
  
## <a name="example"></a>例  
 次のコード例に示します、`InstallChecks`ほど要素は、製品ファイルの使用、[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]します。  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 ときに`InstallChecks`は、評価プロパティを生成します。 は、プロパティを使用し、`InstallConditions`かを判断パッケージがインストール、バイパス、失敗します。 次の表、 `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|存在する場合`FailIf`条件が true に評価されると、パッケージは失敗します。 残りの条件は評価されません。|  
|`BypassIf`|存在する場合`BypassIf`条件が true に評価された、パッケージがバイパスされます。 残りの条件は評価されません。|  
  
## <a name="predefined-properties"></a>定義済みのプロパティ  
 次の表、`BypassIf`と`FailIf`要素。  
  
|プロパティ|メモ|使用できる値|  
|--------------|-----------|---------------------|  
|`Version9X`|Windows 9 X オペレーティング システムのバージョン番号。|4.10 Windows 98 を =|  
|`VersionNT`|Windows NT ベースのオペレーティング システムのバージョン番号。|Major.minor.servicepack です。<br /><br /> 5.0 Windows 2000 を =<br /><br /> 5.1.0 が Windows XP を =<br /><br /> 5.1.2 = Windows XP Professional SP2<br /><br /> 5.2.0 = Windows Server 2003|  
|`VersionNT64`|64 ビット Windows NT ベースのオペレーティング システムのバージョン番号。|前に示したのと同じです。|  
|`VersionMsi`|Windows インストーラー サービスのバージョン番号。|2.0 Windows インストーラー 2.0 を =|  
|`AdminUser`|ユーザーが Windows NT ベースのオペレーティング システムの管理者特権を持つかどうかを指定します。|0 = 管理者特権なし<br /><br /> 1 = 管理者の権限|  
  
 たとえば、Windows 95 が実行されているコンピューターへのインストールをブロックするには、次のようコードを使用します。  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>関連項目  
 [\<コマンド > 要素](../deployment/commands-element-bootstrapper.md)   
 [製品およびパッケージ スキーマ リファレンス](../deployment/product-and-package-schema-reference.md)



