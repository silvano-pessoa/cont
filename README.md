create table transferencia(
  id bigint(20) not null auto_increment,
	numero bigint(20) not null,
	data_transferencia datetime not null,
	empresa_id bigint(20) not null,
	localizacao_origem_id bigint(20) not null,
	localizacao_destino_id bigint(20) not null,
	primary key(id),
	constraint fk_trans_loc_origem foreign key(localizacao_origem_id) references localizacao(id),
	constraint fk_trans_loc_destino foreign key(localizacao_destino_id) references localizacao(id)
);

create table transferencia_item(
	id bigint(20) not null auto_increment,
	transferencia_id bigint(20) not null,
	produto_id bigint(20) not null,
	quantidade numeric(17,4) not null,
	primary key(id),
	constraint fk_trans_item_trans foreign key(transferencia_id) references transferencia(id),
	constraint fk_trans_item_prod foreign key(produto_id) references produto(id)
);