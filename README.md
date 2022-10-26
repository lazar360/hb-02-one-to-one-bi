# hb-02-one-to-one-bi
@Entity
@Table(name="instructor")
public class Instructor {
...
@OneToOne(cascade = CascadeType.ALL)
	@JoinColumn(name="instructor_detail_id") // dans la table, on joint une colonne
	private InstructorDetail instructorDetail;
...
}

@Entity
@Table(name="instructor_detail")
public class InstructorDetail {
...
@OneToOne(mappedBy = "instructorDetail", 
			cascade = {CascadeType.DETACH, CascadeType.MERGE, 
					CascadeType.PERSIST, CascadeType.REFRESH})//TOUT SAUF REMOVE /!\
	private Instructor instructor;
...
}
