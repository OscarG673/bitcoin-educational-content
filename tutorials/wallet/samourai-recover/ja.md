---
name: Samourai Wallet - 復旧方法
description: Samourai Walletに残ってしまったビットコインをどうやって取り戻すか？
---
![cover](assets/cover.webp)

Samourai Walletの創設者が4月24日に逮捕され、サーバーが押収されたことを受け、アプリケーションの一部機能が現在使用できなくなり、自身のDojoを持っていないユーザーはトランザクションをブロードキャストできなくなりました。

最近数日間で複数のユーザーがビットコインを取り戻すのを支援した経験から、Samourai Walletの復旧中に発生する可能性のあるほとんどの問題に遭遇したと思います。したがって、このチュートリアルは、Samourai Walletエコシステム内およびこのインシデントによって影響を受けたソフトウェア内で、まだ利用可能な機能ともはや利用できない機能を特定する状況報告から始めます。次に、Sparrow Walletソフトウェアを使用してSamourai Walletを回復する手順を順を追って進めます。このプロセス中に遭遇する可能性のあるすべての障害を検討し、それらを解決するための解決策を見ていきます。最後に、サーバーの押収に伴うプライバシーへの潜在的なリスクを発見します。

*復旧を支援し、自身の経験を共有してくれた[@Louferlou](https://twitter.com/Louferlou)、そして何がまだ機能しているかを判断するためのテストに貢献してくれたことに、大きな感謝をします。*

## Samourai Walletはまだ機能していますか？

はい、**Samourai Walletアプリはまだ機能しています**が、特定の条件下でのみです。

まず、アプリが以前にスマートフォンにインストールされている必要があります。Google Play Storeからアプリが削除され、APKは押収されたウェブサイトにホストされていたため、現在Samouraiをインストールすることは複雑です。オンラインでAPKを見つけることができるかもしれませんが、ソースが確かでない限りダウンロードすることはお勧めしません。

Samourai WalletのページがGoogle Play Storeで利用できなくなったため、自動更新を無効にすることはできません。アプリがダウンロードプラットフォームに戻った場合、事件の進展に関する詳細情報が得られるまで**自動更新を無効にする**ことが賢明です。

Samourai Walletがすでにスマートフォンにインストールされている場合、アプリにアクセスすることはまだ可能です。Samouraiのウォレット機能を使用するには、Dojoに接続することが不可欠です。以前は、個人のDojoを持たないユーザーはSamouraiのサーバーを介してBitcoinブロックチェーン情報にアクセスし、トランザクションをブロードキャストしていました。これらのサーバーが押収されたことで、アプリはこれらのデータにアクセスできなくなりました。
以前にDojoに接続していなかったが、現在はDojoを持っている場合、アプリケーションにDojoを接続してSamouraiアプリを再び使用するための設定が可能です。バックアップを確認し、ウォレット（アプリケーションではなくウォレット）を削除し、Dojoをアプリケーションに接続してウォレットを復旧する手順については、[このチュートリアルの"_Preparing your Samourai Wallet_" : COINJOIN - DOJO](https://planb.network/en/tutorials/privacy/coinjoin-dojo)セクションを参照してください。
もしSamouraiアプリがすでに自分のDojoに接続されていた場合、ウォレット部分は完璧に機能しています。残高を確認し、トランザクションをブロードキャストすることができます。現在起こっていることにもかかわらず、私はSamourai Walletが現時点で最高のモバイルウォレットソフトウェアであると考えています。個人的には、これからも使用を続ける予定です。
あなたが遭遇する主な問題は、アプリからWhirlpoolアカウントにアクセスできないことです。通常、SamouraiはあなたのWhirlpool CLIとの接続を確立し、これらのアカウントへのアクセスを提供する前にcoinjoinサイクルを開始しようとします。しかし、この接続がもはや可能でないため、アプリはWhirlpoolアカウントへのアクセスを永遠に提供することなく、無限に検索を続けます。この場合、Samouraiに預金アカウントのみを保持しながら、これらのアカウントを別のウォレットソフトウェアで回復することができます。

### Samouraiでまだ利用可能なツールは何ですか？

一方、いくつかのツールはサーバーのシャットダウンによって影響を受けるか、完全に利用不可能です。

個々の支出ツールに関しては、もちろん自分自身のDojoを持っている場合、全てが正常に機能します。通常のStonewallトランザクション（Stonewall x2ではない）は問題なく動作します。

Twitterのコメントでは、Stonewallトランザクションによって提供されるプライバシーが現在減少している可能性が指摘されています。Stonewallトランザクションの付加価値は、構造の面でStonewall x2トランザクションと区別がつかないという事実にあります。アナリストがこの特定のパターンに遭遇した場合、それが単一ユーザーの標準的なStonewallなのか、2人のユーザーを巻き込むStonewall x2なのかを判断することはできません。しかし、以下の段落で見るように、Sorobanの利用不可のためにStonewall x2トランザクションを行うことがより複雑になったため、アナリストは今や任意のトランザクションが通常のStonewallであると仮定するかもしれません。個人的には、この仮定には同意しません。Stonewall x2トランザクションが以前に比べて頻度が低くなるかもしれませんが（そして私はそれがこの事件の前にもすでにそうだったと思います）、それらがまだ可能であるという事実は、それらがないという仮定に基づいた全ての分析を無効にすることができます。
**[-> Stonewallトランザクションについてもっと学ぶ。](https://planb.network/tutorials/privacy/stonewall)**
Ricochetに関しては、Testnet上でDojoを所有していないため、サービスがまだ稼働しているかを確認することができず、権限を持つ可能性のあるウォレットに向けて`100 000 sats`をリスクにさらすことは避けたいと思います。最近このツールをテストする機会があった場合は、この記事を更新できるように私に連絡してください。

Ricochetを使用する必要がある場合は、任意のウォレットソフトウェアでこの操作を手動で実行することができます。様々なホップを適切に手動で実行する方法を学ぶには、この他の記事を参照することをお勧めします：[**RICOCHET**](https://planb.network/tutorials/privacy/ricochet)。

JoinBotツールは、Samouraiが管理するウォレットの参加に完全に依存していたため、もはや稼働していません。

他のタイプの共同トランザクション、しばしば「cahoots」と呼ばれるものに関しては、可能ですが、手動でのみです。サーバーのシャットダウン前には、Stonewall x2やStowaway（PayJoin）トランザクションを実行するために2つのオプションがありました：
- PSBTを自動的かつ遠隔で交換するためにSorobanネットワークを使用する；
- または、複数のQRコードをスキャンしてこれらの交換を手動で実行する。

いくつかのテストの後、Sorobanはもはや機能していないことが明らかになりました。これらの共同トランザクションを実行するためには、データの交換は手動で行わなければなりません。この交換を行うための2つのオプションは以下の通りです：
- もし協力者と物理的に近い場合は、QRコードを順番にスキャンすることができます。
あなたがコラボレーターから遠く離れている場合、PSBTをアプリケーション外の通信チャネルを通じて交換することができます。しかし、これらのPSBTに含まれるデータはプライバシーの面で敏感なので注意してください。交換の機密性を保証するために、暗号化されたメッセージングサービスの使用をお勧めします。
**[-> Stonewall x2トランザクションについてもっと学ぶ。](https://planb.network/tutorials/privacy/stonewall-x2)**

**[-> Stowawayトランザクションについてもっと学ぶ。](https://planb.network/tutorials/privacy/payjoin-samourai-wallet)**

Whirlpoolに関しては、プロトコルはもはや機能していないようです。自分のDojoを持っているユーザーであってもです。この数日間、私は自分のRoninDojoを監視し、いくつかの基本的な操作を試みましたが、Whirlpool CLIはサーバーのシャットダウン以来接続できなくなっています。

しかし、このプロトコルが今後数週間で再活性化されるか、あるいは状況の進展に応じて異なる方法で再考されることを期待しています。この一時停止は、このシステムへの新しいアプローチや潜在的な改善を探求する機会になるかもしれません。
### どの外部ツールがまだ利用可能ですか？
Samourai環境に関連する他のツールについては、いくつかはまだ利用可能ですが、他のものはそうではありません。

無料のチェーン分析ウェブサイトOXT.meは、残念ながら現在利用できなくなっています。

Whirlpool Stats Toolは、SamouraiのGitLabにホストされていたため、もはやダウンロードできません。以前にこのPythonツールをローカルマシンにダウンロードしていた場合や、RoninDojoノードにインストールしていた場合でも、WSTは当面の間機能しません。実際、その運用はOXT.meが提供するデータに依存しており、このサイトはもはやアクセスできません。現在、Whirlpoolプロトコルが非アクティブであるため、WSTは特に役に立ちません。

KYCP.orgサイトは、現在アクセスできなくなっています。

Boltzmann Calculator PythonツールのコードをホストしていたGitLabも押収されました。したがって、現時点ではこのツールをダウンロードすることはできません。しかし、RoninDojoを持っている場合は、以前と同じようにBoltzmann Calculatorを使用し続けることができます。

RoninDojoに関しては、Whirlpool CLIやWSTなどの特定のツールが利用できないにもかかわらず、このノードインボックスソフトウェアは正常に機能しています。FulcrumやElectrsのおかげで、他のウォレットソフトウェアにも引き続き使用できます。RoninDojoについての詳細情報を得たい場合や、特定の質問がある場合は、[彼らのTelegramグループ](https://t.me/RoninDojoNode)に参加することをお勧めします。

しかし、RoninDojoのソースコードは、SamouraiのGitLabにホストされていたため、現在はアクセスできなくなっています。したがって、現時点ではRaspberry Piに手動でインストールすることはできません。

ウォッチオンリーウォレットソフトウェアのSentinelについては、Samouraiアプリと同様の状況です。自分のDojoを持っている場合は、問題なくSentinelを使用し続けることができます。しかし、Dojoを持っていない場合は、接続を確立することができなくなります。Samouraiとは異なり、Sentinelのウェブサイトは依然としてオンラインでアクセス可能です。しかし、このサイトとそこで提供されているAPKには注意してください。現在これらのリソースを誰が管理しているのかは不明です。

### Sparrow Walletは影響を受けていますか？
Sparrow Walletは通常通り動作していますが、Samouraiツールはもう利用できなくなりました。現在、Sparrowを介してcoinjoinsを実行することはできません。同様に、共同支出ツールももはやアクセスできません。SparrowはSamouraiとは異なり、PSBTの手動交換オプションを提供していません。他のすべての機能については、Sparrowは問題なく動作します。必要に応じて、このソフトウェアを使用してSamouraiウォレットを回復することもできます。

## Samouraiウォレットを回復する方法は？
前のセクションで見たように、自分自身のDojoを所有している場合、ソフトウェアを切り替える必要は必ずしもありません。**Samouraiは日常の支出に優れたホットウォレットの選択肢です。**しかし、Dojoを持っていない場合や、別のソフトウェアを選択したい場合は、潜在的な障害について詳しく説明しながら、完全な回復プロセスを説明します。

いずれにせよ、時間をかけて慎重に行い、間違いを犯さないようにすることが重要です。急ぐ必要はありません。プライベートキーを保持しているため、Samouraiのサーバーが押収されても、これには何の影響もありません。何が起こっても、彼らがあなたのプライベートキーにアクセスすることは明らかにできません。

### パスフレーズを確認する

ウォレットを回復するには、バックアップファイル経由での回復を選択しても、パスフレーズを持っている必要があります。まず、このパスフレーズの有効性を確認します。Samourai Walletアプリを開き、左上のPaynymアイコンをクリックし、`Settings`を選択します。

![samourai](assets/1.webp)

次に、`Troubleshooting`をクリックし、その後に`Passphrase/backup test`を選択します。

![samourai](assets/2.webp)

パスフレーズを入力し、`Ok`をクリックします。正しい場合、Samouraiがそれを確認します。後で使用する予定がある場合は、バックアップファイルも確認するオプションがあります。

![samourai](assets/3.webp)

このステップはオプショナルですが、推奨されます。パスフレーズが正しいことを確認し、後で問題の潜在的な原因を排除します。この段階でSamouraiがパスフレーズが間違っていると示した場合、回復は不可能です。パスフレーズを正しく入力したことを確認し、再度チェックしてください。

### オプション1: バックアップファイルを使用してSparrowでウォレットを回復する

Sparrow Walletのバージョン1.8.6以降、アプリケーションが自動的に生成する`samourai.txt`というバックアップテキストファイルを使用して、Samouraiウォレットを直接インポートすることが可能です。このファイルにはウォレットを回復するために必要なすべての情報が含まれており、セキュリティのためにパスフレーズで暗号化されています。

このオプションを選択する場合、最新の`samourai.txt`ファイルとパスフレーズが必要です。Samourai Walletでこのファイルを生成するには、右上の三つの小さな点をクリックし、`Export wallet backup`を選択します。

![samourai](assets/4.webp)
次に、`Export to Clipboard`を選択します。その後、このファイルをPCに安全に転送する必要があります。ファイルは暗号化されていますが、パスフレーズだけで解読できるため、転送中の予防措置を講じることが重要です。プレーンテキストとして直接転送する場合は、PC上に`samourai.txt`ファイルを作成し、クリップボードの内容をそれに貼り付ける必要があります。別の方法としては、電話に保存されているファイルから直接`samourai.txt`ファイルを取得することもできます。
PC上でファイルにアクセスできるようになったら、Sparrow Walletを開き、`File`タブをクリックし、`Import Wallet`を選択してウォレットのインポートを開始します。

![samourai](assets/5.webp)
`Samourai Backup`までスクロールダウンし、`Import File`をクリック、そしてあなたの`samourai.txt`ファイルを選択してください。
![samourai](assets/6.webp)

その後、Sparrowはファイルを復号するためのパスワードを求めます。このパスワードは実際にはあなたのパスフレーズです。対応するフィールドに入力し、`Import`をクリックしてください。

![samourai](assets/7.webp)

この段階で、あなたのウォレットが表示されない場合、`samourai.txt`ファイルのコピー時またはパスフレーズの入力時に間違いがあった可能性があります。より多くの助けが必要な場合は、トラブルシューティングセクションを参照してください。

![samourai](assets/8.webp)

スクリプトタイプについて、Samouraiで他のスクリプトを設定していない場合、通常はSegWit V0（ネイティブSegWit / P2WPKH）のみを使用すべきです。このデフォルトスクリプトを保持し、`Import`をクリックしてください。

![samourai](assets/9.webp)

例えば、「Samourai Recovery」としてあなたのウォレットに名前を付け、`Create Wallet`をクリックしてください。

![samourai](assets/10.webp)

その後、Sparrowはパスワードの選択を求めます。このパスワードはこのPC上でのウォレットへのアクセスを保護するだけで、ウォレットのキーの導出には関係ありません。強力なパスワードを選び、覚えておくためにメモを取り、`Set Password`をクリックしてください。

![samourai](assets/11.webp)

その後、Sparrowはあなたのウォレットのキーを導出し、対応するトランザクションを検索します。

![samourai](assets/12.webp)

現時点では、あなたの預金口座のみがアクセス可能です。もしあなたがこの口座のみにSamouraiを使用していた場合、すべての資金を見ることができるはずです。しかし、Whirlpoolも使用していた場合は、`premix`、`postmix`、`badbank`口座を導出する必要があります。Sparrowでは、`Settings`タブをクリックし、次に`Add Accounts...`をクリックしてください。

![samourai](assets/13.webp)
開いたウィンドウで、ドロップダウンメニューから`Whirlpool Accounts`を選択し、`OK`をクリックしてください。
![samourai](assets/14.webp)

その後、様々なWhirlpool口座が表示され、Sparrowは関連するビットコインを使用するために必要なキーを導出します。

![samourai](assets/15.webp)

Sparrow以外のソフトウェア、例えばElectrumを使用してSamouraiウォレットを回復する場合、手動回復のためのWhirlpoolアカウントインデックスは以下の通りです：
- 預金：`m/84'/0'/0'`
- Bad Bank：`m/84'/0'/2147483644'`
- Premix：`m/84'/0'/2147483645'`
- Postmix：`m/84'/0'/2147483646'`

これで、Sparrow上であなたのビットコインにアクセスできるようになりました。Sparrow Walletの使用方法について助けが必要な場合は、[専用のチュートリアル](https://planb.network/tutorials/wallet/sparrow)もチェックしてみてください。

また、SamouraiであなたのUTXOに関連付けられたラベルを手動でインポートすることをお勧めします。これにより、その後のSparrowで効果的なコインコントロールを実行できます。

### オプション2：ニーモニックフレーズでSparrow上でウォレットを回復する

バックアップファイルでの回復を行いたくない場合は、12語のリカバリーフレーズとあなたのパスフレーズを使用する、より伝統的な方法を選択することができます。この第二のオプションはしばしばよりシンプルです。
まず、リカバリーフレーズとパスフレーズを手元に用意してください。次に、Sparrow Walletソフトウェアを開き、`File`タブをクリックし、`Import Wallet`を選択してウォレットのインポートを開始します。
![samourai](assets/16.webp)

`Mnemonic Words (BIP39)`を選択し、ドロップダウンメニューから`Use 12 Words`をクリックします。

![samourai](assets/17.webp)

リカバリーフレーズの12の単語を正しい順序で入力します。

![samourai](assets/18.webp)

Sparrowが`Invalid Checksum`メッセージを表示した場合、リカバリーフレーズのチェックサムが無効であることを示しており、単語の入力時に間違いがあった可能性があります。

![samourai](assets/19.webp)

フレーズが正しい場合は、`Use Passphrase?`ボックスをチェックし、専用のフィールドにパスフレーズを入力します。最後に、すべてが正しければ、`Discover Wallet`ボタンをクリックします。

![samourai](assets/20.webp)

例えば「Samourai Recovery」という名前をウォレットに付け、`Create Wallet`をクリックします。

![samourai](assets/21.webp)
その後、Sparrowはパスワードの選択を求めます。このパスワードはPC上でのウォレットへのアクセスを保護するものであり、ウォレットのキーの導出には関係ありません。強力なパスワードを選び、覚えておくために書き留め、`Set Password`をクリックしてください。
![samourai](assets/22.webp)

Sparrowはその後、ウォレットのキーを導出し、対応するトランザクションを検索します。

![samourai](assets/23.webp)

この段階でウォレットが表示されない場合、パスフレーズまたはリカバリーフレーズの入力時に間違いがあった可能性があります。より多くの助けを得るために、専用のトラブルシューティングセクションを参照してください。

現時点では、預金口座のみがアクセス可能です。この口座のみをSamouraiで使用していた場合、すべての資金が表示されるはずです。しかし、Whirlpoolも使用していた場合は、`premix`、`postmix`、`badbank`口座を導出する必要があります。Sparrowでは、`Settings`タブをクリックし、`Add Accounts...`を選択します。

![samourai](assets/24.webp)

開いたウィンドウで、ドロップダウンリストから`Whirlpool Accounts`を選択し、`OK`をクリックします。

![samourai](assets/25.webp)

すると、さまざまなWhirlpool口座が表示され、Sparrowは関連するビットコインを使用するために必要なキーを導出します。

![samourai](assets/26.webp)

SamouraiウォレットをElectrumなどの別のソフトウェアで復旧する場合、手動復旧のためのWhirlpool口座インデックスは以下の通りです：
- Deposit: `m/84'/0'/0'`
- Bad Bank: `m/84'/0'/2147483644'`
- Premix: `m/84'/0'/2147483645'`
- Postmix: `m/84'/0'/2147483646'`

これで、Sparrow上でビットコインにアクセスできるようになりました。Sparrow Walletの使用方法について助けが必要な場合は、[専用のチュートリアル](https://planb.network/tutorials/wallet/sparrow)も参照してください。

また、SamouraiでUTXOsに関連付けたラベルを手動でインポートすることをお勧めします。これにより、その後のSparrowで効果的なコインコントロールを実行できます。

### 一般的に遭遇する問題は何ですか？
過去数日間で複数の人々を支援した後、私はあなたのウォレットの回復を妨げる可能性のあるほとんどの問題に遭遇したと信じています。以前のチュートリアルにもかかわらず、まだウォレットにアクセスできない場合は、いくつかの追加の推奨事項があります。まず第一に、回復が機能するためには、回復フレーズが正確であることが絶対に必要です。12語のフレーズを見つけることができない場合は、*オプション1* を使用してSamouraiのバックアップファイルから回復することができます。また、`Settings`に移動し、`Wallet`を選択し、最後に`Show 12-word recovery phrase`を選択することで、Samourai Wallet内で直接回復フレーズにアクセスすることもできます。

次に、回復中にパスフレーズを入力する際のタイピングエラーは、誤った派生キーをもたらし、Sparrow上でのウォレットの回復を妨げます。**パスフレーズは完全に正確でなければなりません！**

これを解決するために、まずこの記事の「_パスフレーズの検証_」セクションに記載されているように、Samouraiアプリケーションでパスフレーズの有効性を確認することをお勧めします：
1. **Samouraiでの検証：** Samouraiがパスフレーズが正しいと確認した場合、最初から回復を再試行し、Sparrowでパスフレーズを間違いなく正確に入力してください；
2. **パスフレーズエラー：** Samouraiがパスフレーズが間違っていると示した場合、Sparrowでの試みを続けることは無意味です。正しいパスフレーズが見つからない限り、ウォレットの回復は不可能です。パスフレーズを永久に失った場合は、Samouraiアプリケーションを安全に保管してください。サーバーが再起動されることを期待して、回復なしでアプリケーションから直接支出を行うことができるだけです。**この場合、Dojoに接続しようとしないでください**、これはSamouraiでウォレットをリセットすることを意味し、パスフレーズへのアクセスが必要です。

他に遭遇したエラーの中には、多くがSparrowのネットワーク構成に関連しています。

まず、Sparrowが`mainnet`モードではなく`testnet`モードで正しく構成されていることを確認してください。実際、SparrowがTestnetでトランザクションを検索する場合、何も見つかりません。なぜなら、あなたのウォレットはMainnetにあるからです。Testnetは、テストと開発のためにのみ使用されるBitcoinの代替バージョンであり、独自のブロックとトランザクションを持つメインネットワーク（Mainnet）から別のネットワークで動作します。どのネットワークにいるかを確認するには、`Tools`タブをクリックし、`Restart In`を選択します。`Mainnet`オプションが表示されている場合、メインネットワークにいないことになります。それを選択してSparrowをMainnetで再起動し、回復プロセスを再開してください。

![samourai](assets/27.webp)
また、Sparrowを自分のノードに接続する際に困難を経験した人もいます。Sparrowの右下にある色付きのスイッチは、ソフトウェアがBitcoinノードに正しく接続されているかどうかを示します。Samouraiトランザクションを取得するには、ソフトウェアがうまく接続されていることが不可欠です。下の画像のようにスイッチがアクティブになっていることを確認してください（公開ノードは黄色、Bitcoin Coreは緑、Electrumサーバーは青）。
![samourai](assets/28.webp)

スイッチがアクティブになっていない場合は、それをクリックして接続を再アクティブ化してください。

![samourai](assets/29.webp)

問題が解決しない場合は、以下の解決策が考えられます：
- 自分のElectrumサーバー（青）またはBitcoin Core（緑）に接続しようとしていてSparrowが接続できない場合は、`File > Preferences... > Server`の下の接続情報を確認してください。

![samourai](assets/30.webp)
接続問題が続く場合、ノードの同期が完全には完了していない可能性があります。ノードとインデクサーが100%同期していることを確認してください。最終手段として必要な場合は、ノードをSparrowから切断し、公開ノードに接続してください。公開ノードに既に接続していて接続に失敗した場合は、ドロップダウンリストから別のノードを選択してノードを変更してみてください。

![samourai](assets/31.webp)

ウォレットの回復に成功したが、不完全なように見える場合、派生に関連する問題があるかもしれません。

`P2WPKH`以外の異なるスクリプトタイプを使用してSamourai預金アカウントを使用した場合に問題が発生する可能性があります。Samouraiはデフォルトでこのスクリプトタイプを使用しますが、手動で変更した場合は、Sparrowで回復する際にこれも調整する必要があります。

他のスクリプトタイプの枝を派生させるには、使用した各スクリプトタイプについて回復プロセスを繰り返す必要があります。これを行うには、Sparrowで`File > New Wallet`に移動し、ドロップダウンリストから別のスクリプトタイプを選択し、`New or Imported Software Wallet`をクリックし、初期チュートリアルと同じ手順に従ってください。

![samourai](assets/32.webp)

私が遭遇した別の派生問題は、Gap Limit値に関連しています。この値は、Sparrowが新しいアドレスの派生を停止するべき空のアドレスの数を示します。回復後にいくつかの取引が欠落していることに気付いた場合、これはGap Limitが低すぎるためかもしれません。これを解決するには、問題を引き起こしているアカウント（例えば、ポストミックスアカウント）に移動し（複数のアカウントが関係している場合は、この操作を各アカウントに対して繰り返します）。

![samourai](assets/33.webp)

`Settings`タブをクリックし、次に`Advanced...`ボタンをクリックします。
![samourai](assets/34.webp)
例えば、ここでは`400`に設定するなど、Gap Limitの値を徐々に増やします。その後、`Close`ボタンをクリックします。

![samourai](assets/35.webp)

`Apply`をクリックして最終化します。Sparrowはより多くのアドレスを派生させ、それらの上で資金を検索することになり、これによりすべての取引を回復するのに役立ちます。

![samourai](assets/36.webp)

これで、過去数日間に遭遇したさまざまな回復問題をカバーしました。これらの解決策をすべて試してもまだ問題が解決しない場合は、[Discover Bitcoin Discord](https://discord.gg/xKKm29XGBb)に参加して助けを求めることをお勧めします。私は定期的にこのDiscordを訪れ、解決策があれば喜んで助けます。他のビットコイナーも彼らの経験を共有し、支援を提供することができます。**いずれにせよ、回復フレーズ、バックアップファイル、およびパスフレーズを秘密に保つことが不可欠です**。これらを誰かと共有すると、ビットコインを盗まれる可能性があります。

回復が完了すると、ビットコインにアクセスできるようになります。それは良いことですが、それだけでは不十分かもしれません。実際、サーバーの押収はプライバシーに対する新たな潜在的リスクを引き起こします。次のセクションでは、これらのリスクを詳細に検討し、プライバシーを保護するために取るべき予防策を概説します。

## あなたの取引のプライバシーに対する影響は何ですか？

### Dojoを接続していないSamouraiユーザーとして

自分のDojoを接続せずにSamourai Walletを使用していた場合、アプリが機能するためにはxpubsをSamouraiのサーバーに通知する必要がありました。これらのサーバーの押収により、当局がこれらのxpubsにアクセスできるようになった可能性があります。
このシナリオは仮定の話です。これらのxpubが記録されたか、潜在的な保管が破壊されたか、当局がそれらを回収したか、そしてそれらをチェーン分析に使用する計画があるかどうかはわかりません。しかし、このような状況では、最悪のシナリオを考慮することが賢明です。つまり、自分のDojoに接続していないユーザーのxpubを当局が持っている場合です。参考までに、xpubは子公開鍵（公開鍵+チェーンコード）を生成するために必要なすべての要素を含む文字列です。これは、階層的決定性ウォレットで受信アドレスを生成し、関連する秘密鍵を公開することなくアカウントのトランザクションを観察するために使用されます。これにより、例えば「監視専用」ウォレットの作成が可能になります。しかし、xpubを公開することは、第三者がトランザクションを追跡し、関連するアカウントの残高を確認できるようになるため、ユーザーのプライバシーを損なう可能性があります。
あなたのxpubを知っている人は、あなたのウォレットのすべての受信アドレス、過去に使用されたもの、そして将来生成されるものを見ることができます。

Dojoを持たないユーザーにとって、xpubの潜在的な漏洩は二つの主な結果をもたらします：
- プライバシーの観点から効果がなくなるため、xpubを知っている人にとっては、行ったcoinjoinが無効になり、あなたのコインはすべての匿名性を失います；
- この人はまた、あなたのSamourai Walletのすべての受信アドレスを追跡することもできます。

したがって、最悪のシナリオを考慮し、プライバシーの面で潜在的に危険にさらされているこのウォレットと別れることが重要です。これを行うには、Sparrow Walletのような別のソフトウェアで最初から新しいウォレットを作成します。バックアップの有効性を確認した後、トランザクションを行ってすべての資金を転送します。この操作はコインの追跡リンクを断ち切るわけではありませんが、新しいウォレットのアドレスを当局が確実に知ることを防ぎます。

この転送操作中に、コインの統合を避けることをお勧めします。xpubが危険にさらされていると仮定すると、xpubにアクセスできる人の観点からは、あなたのプライバシーは既に危険にさらされているため、統合は影響を与えません。しかし、他の人からのプライバシーを守るために、コインをあまり統合しすぎないようにすることをお勧めします。最悪の場合、当局だけがあなたのxpubにアクセスできるかもしれませんが、世界の残りの部分はそれについて知りません。したがって、他の人の観点からは、コインを統合することはCommon Input Ownership Heuristic（CIOH）のために、あなたのプライバシーに大きな害を与える可能性があります。

最後に、追跡を完全に断ち切るために、この新しいウォレットからcoinjoinを実行することも検討してください。
**警告：** 単にSamourai walletをSparrow Walletに取り込むだけでは不十分です。漏洩した可能性のあるxpubを使用しないようにするためには、新しいリカバリーフレーズで完全に新しいウォレットを作成する必要があります。既存のシードをSparrowにインポートした場合、ウォレット管理ソフトウェアを変更するだけで、ウォレット自体は変わりません。

### SparrowまたはSamourai with Dojoのユーザーとして

ウォレットがSparrow Walletでのみ管理されている場合、公開ノードを使用しているか自分のBitcoinノードを使用しているかにかかわらず、xpubは漏洩していない可能性があります。同様に、Samouraiアプリを使用しており、ウォレットの作成以来、このアプリを常に自分のDojoに接続している場合、xpubも安全です。
しかし、自身のDojoを持たずに同じウォレットを使用していた期間があり、その後で自身のDojoを持つようになった場合、Samouraiのサーバーがあなたのxpubsにアクセスしていた可能性があり、その結果、当局がそれらを知ることができたかもしれません。この特定の状況にある場合は、前のセクションの推奨事項に従い、xpubsを危険にさらされたものとみなすことをお勧めします。
自身のDojoを持って常にSparrowやSamouraiを使用していた人々にとって、主なリスクは、コインの匿名性セットが潜在的に減少する可能性があることです。最悪のシナリオを想定して、Dojoを持たない全ユーザーのxpubsが当局の手に渡っている場合、これらの当局によってコインのコインジョインサイクルを通じた経路が追跡される可能性があります。

これを具体例で説明しましょう。最初のコインジョインサイクルに参加し、その後2つの追加の下流コインジョインサイクルに参加したと想像してください。Dojoを持たないユーザーのxpubsが漏洩していなければ、あなたのコインの見込み匿名性セットは13になります。

![samourai](assets/37.webp)

しかし、xpubsが漏洩したと考え、初期のコインジョインでDojoを持たないユーザーに遭遇し、その後の最初の下流コインジョインで2人に遭遇した場合、当局の視点から見たあなたの見込み匿名性セットは13ではなく10になるだけです。

![samourai](assets/38.webp)
この匿名性セットの潜在的な減少は、多くの要因に依存するため、定量化するのが複雑です。そして、各コインは異なる影響を受けます。例えば、初期のサイクルで遭遇したDojoを持たないユーザーは、後のサイクルで遭遇したユーザーよりも見込み匿名性セットに大きな影響を与えます。状況を想像してもらうために、これは仮説的なものですが、Samouraiが提供した最新の統計によると、コインジョインに関わるコインの85%から90%がDojo、Sparrow、またはBitcoin Keeperを持つユーザーから来ており、これらのユーザーは、最悪のシナリオであっても、xpubsが漏洩していないとされています。
これらの数字は検証が難しいものの、2つの理由で私には一貫しているように思えます：
- Sparrow Walletが広く使用されている；
- ほとんどのノード・イン・ボックスソフトウェアはDojoの実装を提供しており、Umbrelのような主流のソフトウェアは現在非常に人気があります。

したがって、いくつかの側面を考慮する必要があります。あなたのコインのプライバシーが当局に対して非常に重要である場合、最悪のシナリオに備えることが賢明であり、Dojoを持たないユーザーからのxpubsの潜在的な漏洩によって、あなたのWhirlpoolコインジョインサイクルが追跡される可能性が100%保証されないことは難しいです。この仮定は非常にありそうにないものの、不可能ではありません。

一方で、これらのxpubsを保有する可能性のある当局に対して、あなたのコインのプライバシーがそれほど重要でない場合は、状況を異なる角度から考えることができます。

「当局に対して」と明記するのは、サーバーを押収した当局のみがこれらのxpubsを潜在的に知っている可能性があるため重要です。もし、あなたがコインジョインを使用する目的が、あなたの資金を追跡できるようにするためではなく、あなたの銀行があなたの資金を追跡できないようにすることであった場合、その銀行はサーバーの押収前と同じくらい情報を持っていません。
最終的に、サーバーの押収前に、あなたのコインの初期匿名セットを考慮することが不可欠です。例として、見込みの匿名セットが40,000に達したコインを取り上げてみましょう。この匿名セットの潜在的な減少は、おそらく無視できるでしょう。実際、すでに非常に高い基本匿名セットを持っているため、Dojoを持たない数人のユーザーの存在が状況を根本的に変える可能性は低いです。しかし、あなたのコインの匿名セットが40だった場合、この潜在的なリークはあなたの匿名セットに深刻な影響を与え、追跡を可能にするかもしれません。OXT.meのシャットダウンに伴いWSTツールがサービスを提供していない現在、これらの匿名セットを推定することしかできません。振り返りの匿名セットについては、Whirlpoolモデルが最初のコインジョインから非常に高いことを保証しているため、あまり心配する必要はありません。唯一の問題が発生する可能性があるのは、あなたのコインが数年間リミックスされておらず、プールの開始時に混合された場合です。見込みの匿名セットに関しては、あなたのコインがコインジョインに利用可能だった期間を調べることができます。数ヶ月間だった場合、おそらく非常に高い見込みの匿名セットを持っているでしょう。逆に、サーバーが押収される数時間前にプールに追加された場合、その見込みの匿名セットはおそらく非常に低いでしょう。
[**-> 匿名セットとその計算方法についてもっと学ぶ。**](https://planb.network/tutorials/privacy/wst-anonsets)

もう一つ考慮すべき側面は、混合されたコインの匿名セットに対する統合の影響です。WhirlpoolアカウントがSamouraiアプリ経由でアクセスできなくなったため、多くのユーザーが他のソフトウェアにウォレットを移行し、Whirlpoolから資金を引き出そうとした可能性が高いです。特に、先週末にはBitcoinネットワークの取引手数料が比較的高かったため、ポストミックスコインを統合する強い技術的および経済的インセンティブがありました。これは、多くのユーザーが大規模な統合を行った可能性が高いことを意味します。

これらのポストミックス統合の問題は、それらが常に匿名セットを減少させることであり、それを実行するユーザーだけでなく、彼らがコインジョインサイクル中に遭遇したユーザーにとってもそうです。この現象を正確に検証または定量化することはできませんでしたが、その時点での取引手数料に関連する経済的インセンティブから、匿名セットが潜在的に低いと考えることができます。

### センチネルユーザーとして

ウォッチオンリーウォレットアプリケーションであるSentinelのネットワーク運用はSamouraiと似ています。ウォレット情報にアクセスするためには、アプリケーションが提供したxpubs、公開鍵、およびアドレスをDojoに送信する必要があります。常に自分のDojoをSentinelで使用していた場合は問題ありませんし、引き続きアプリケーションを心配なく使用できます。しかし、Samouraiのサーバーに依存していた場合、xpubsが露出している可能性があります。この場合、Samourai WalletがSamouraiのサーバーに接続されたときに推奨される同じウォレット変更プロセスに従うことが望ましいです。

SamouraiではあなたのDojoを使用していたがSentinelでは使用していなかったというありそうにない事態であれば、xpubsが危険にさらされていると考える方が賢明でしょう。

## 結論
この記事を最後まで読んでいただきありがとうございます。情報が不足していると思われる場合や、提案がある場合は、遠慮なく私に連絡してご意見を共有してください。さらに、このチュートリアルにもかかわらず、Samourai Walletの回復にさらなる支援が必要な場合は、[the Discover Bitcoin Discord](https://discord.gg/xKKm29XGBb)に参加して助けを求めることをお勧めします。私は定期的にこのDiscordを訪れており、解決策を持っている場合は喜んでお手伝いします。他のビットコイナーも、彼らの経験を共有し、サポートを提供することができます。**いずれにせよ、リカバリーフレーズ、バックアップファイル、およびパスフレーズを秘密に保つことが極めて重要です**。これらを誰かと共有すると、ビットコインを盗まれる可能性があります。